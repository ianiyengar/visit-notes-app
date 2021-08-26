<template>
  <div class="signup">
    <form v-on:submit.prevent="submit()">
      <h1>Signup</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Name:</label>
        <input type="text" v-model="name" />
        <br />
        <small>{{ 20 - name.length }} characters remaining</small>
      </div>
      <div>
        <label>Email:</label>
        <input type="email" v-model="email" />
      </div>
      <div>
        <label>Password:</label>
        <input type="password" v-model="password" />
        <br />
        <small v-if="password.length > 0 && password.length < 6" class="text-danger">
          Must be at least 6 characters
        </small>
      </div>
      <div>
        <label>Password confirmation:</label>
        <input type="password" v-model="passwordConfirmation" />
        <br />
        <small v-if="password !== passwordConfirmation" class="text-danger">Passwords must match!</small>
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>
