<template>
  <div class="home">
    <h1>New Note</h1>
    <div>
      Name:
      <input type="text" v-model="newNote.name" />
      Date:
      <input type="text" v-model="newNote.date" />
      Content:
      <input type="text" v-model="newNote.content" />
      <button v-on:click="createNote()">Create Note</button>
    </div>
    <h1>All Notes</h1>
    <div v-for="note in notes" v-bind:key="note.id">
      <h2>{{ note.name }}</h2>
      <img v-bind:src="note.url" v-bind:alt="note.name" />
      <p>Date: {{ note.date }}</p>
      <p>Content: {{ note.content }}</p>
      <button v-on:click="showNote(note)">More info</button>
    </div>
    <dialog id="note-details">
      <form method="dialog">
        <h1>Note info</h1>
        <p>
          Name:
          <input type="text" v-model="currentNote.name" />
        </p>
        <p>
          Date:
          <input type="text" v-model="currentNote.date" />
        </p>
        <p>
          Content:
          <input type="text" v-model="currentNote.content" />
        </p>
        <button v-on:click="updateNote(currentNote)">Update</button>
        <button>Close</button>
      </form>
    </dialog>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      notes: [],
      newNote: {},
      currentNote: {},
    };
  },
  created: function () {
    this.indexNotes();
  },
  methods: {
    indexNotes: function () {
      axios.get("/notes").then((response) => {
        console.log("notes index", response);
        this.notes = response.data;
      });
    },
    createNote: function () {
      var params = {
        name: this.newNote.name,
        date: this.newNote.date,
        content: this.newNote.content,
      };
      axios
        .post("/notes", params)
        .then((response) => {
          console.log("notes create", response);
          this.notes.push(response.data);
          this.newNote = {};
        })
        .catch((error) => {
          console.log("notes create error", error.response);
        });
    },
    showNote: function (note) {
      this.currentNote = note;
      document.querySelector("#note-details").showModal();
    },
    updateNote: function (note) {
      var params = {
        name: note.name,
        date: note.date,
        content: note.content,
      };
      axios
        .patch("/notes/" + note.id, params)
        .then((response) => {
          console.log("notes update", response);
          this.currentPhoto = {};
        })
        .catch((error) => {
          console.log("notes update error", error.response);
        });
    },
    destroyNote: function (note) {
      axios.delete("/notes/" + note.id).then((response) => {
        console.log("notes destroy", response);
        var index = this.notes.indexOf(note);
        this.notes.splice(index, 1);
      });
    },
  },
};
</script>
