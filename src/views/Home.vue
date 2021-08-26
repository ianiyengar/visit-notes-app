<template>
  <div class="home">
    <h1>New Note</h1>
    <div>
      Name:
      <input type="text" v-model="newNote.name" />

      Date:
      <input type="text" v-model="newNote.date" />
      <br />
      <br />
      <span>Goals addressed:</span>
      <br />
      <input type="checkbox" id="pronunciations " value="pronunciations " v-model="newNote.pronunciations" />
      <label for="pronunciations ">Pronunciations</label>
      <br />
      <input type="checkbox" id="reach/grasp/manipulation" value="reach/grasp/manipulation" v-model="newNote.reach" />
      <label for="reach/grasp/manipulation">Reach, Grasp, and Manipulation</label>
      <br />
      <input type="checkbox" id="+" value="+" v-model="newNote.metgoal" />
      <label for="+">+ (Goal Met)</label>
      <br />
      <input type="checkbox" id="-" value="-" v-model="newNote.needswork" />
      <label for="-">- (Needs Work)</label>
      <br />

      <br />
      Content:
      <!-- <input type="text" v-model="newNote.content" /> -->
      <textarea
        input
        type="text"
        v-model="newNote.content"
        id="txtComment"
        placeholder="Enter your note here"
        class="form-control long-input-field required chars"
        data-name="Comment"
        data-maxcharid="chars-counter-comment"
        maxlength="1000000"
        rows="4"
      ></textarea>
      <br />
      <button class="btn btn-primary" v-on:click="createNote()">Create Note</button>
    </div>
    <br />
    <h1>All Notes</h1>
    <div v-for="note in notes" v-bind:key="note.id">
      <h2>{{ note.name }}</h2>
      <p>Date: {{ note.date }}</p>
      <p>Pronunciations: {{ note.pronunciations }}</p>
      <p>Reach: {{ note.reach }}</p>
      <p>Met Goal: {{ note.metgoal }}</p>
      <p>Needs Work: {{ note.needswork }}</p>
      <p>Content: {{ note.content }}</p>
      <button class="btn btn-primary" v-on:click="showNote(note)">More info</button>
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
          <textarea
            input
            type="text"
            v-model="currentNote.content"
            id="txtComment"
            placeholder="Enter your note
          here"
            class="form-control long-input-field required chars"
            data-name="Comment"
            data-maxcharid="chars-counter-comment"
            maxlength="1000000"
            rows="2"
          />
        </p>
        <button v-on:click="updateNote(currentNote)">Update</button>
        <button v-on:click="destroyNote(currentNote)">Destroy Note</button>
        <button>Close</button>
      </form>
    </dialog>
  </div>
</template>

<style>
.home {
  padding: 16px;
}
</style>

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
        pronunciations: this.newNote.pronunciations,
        reach: this.newNote.reach,
        metgoal: this.newNote.metgoal,
        needswork: this.newNote.needswork,
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
    // ADD CHECK BOX
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
