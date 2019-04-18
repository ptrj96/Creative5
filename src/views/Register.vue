<template>
<div>
  <h1>Register for an account</h1>
  <form @submit.prevent="register" class="input-form">
    <fieldset>
      <p>All fields are required.</p>

      <div class="input-field">
        <label for="name">Real Name</label>
        <input v-model="name" type="text" placeholder="Real Name">
      </div>

      <div class="input-field">
        <label for="username">Username</label>
        <input v-model="username" type="text" placeholder="Username">
      </div>

      <div class="input-field">
        <label for="password">Password</label>
        <input v-model="password" type="password" placeholder="Password">
      </div>

      <div class="input-field">
        <label for="birthday">Birthday</label>
        <input v-model="birthday" type="date" placeholder="Birthday">
      </div>

      <div class="button-div">
        <button type="submit" class="pure-button pure-button-primary">Submit</button>
      </div>
    </fieldset>
  </form>
  <p v-if="error" class="error">{{error}}</p>
</div>
</template>

<script>
import moment from 'moment';

export default {
  name: 'register',
  data() {
    return {
      name: '',
      username: '',
      password: '',
      birthday: '',
      error: '',
    }
  },
  methods: {
    async register() {
      try {
        let test = moment(this.birthday, 'YYYY-MM-DD');
        this.error = await this.$store.dispatch("register", {
          name: this.name,
          username: this.username,
          password: this.password,
          birthday: test.toDate(),
        });
        if (this.error === "")
          this.$router.push('/');
      } catch (error) {
        console.log(error);
      }
    }
  }
}
</script>

<style scoped>
form {
  border: 1px solid #ccc;
  background-color: #eee;
  border-radius: 4px;
  padding: 20px;
}

.pure-controls {
  display: flex;
}

.pure-controls button {
  margin-left: auto;
}
</style>
