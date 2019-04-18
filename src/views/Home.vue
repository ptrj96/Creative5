<template>
  <div class="home">
    <div v-if="user">
      <div class="header">
        <div v-if="this.birthday === this.todaysDate">
          <h1>Yes it is your birthday!!</h1>
          <img src="http://i.imgur.com/9umnm.gif" alt="">
        </div>
        <div v-else>
          <h1>No</h1>
          <h2>Your birthday is {{this.birthday}}</h2>
          <h2>Today is {{this.todaysDate}}</h2>
          <p></p>
        </div>
        <a href="#" @click="logout"><i>Logout</i></a>

      </div>
    </div>
    <div v-else>
      <h2>Log in to see if it is your birthday!</h2>
      <router-link to="/register" class="pure-button">Register</router-link> or
      <router-link to="/login" class="pure-button">Login</router-link>
    </div>
  </div>
</template>

<script>
import moment from 'moment';
// @ is an alias to /src

export default {
  name: 'home',
  components: {

  },
  computed: {
    user() {
      return this.$store.state.user;
    },
    birthday() {
      return this.$store.state.birthday;
    },
    todaysDate() {
      return moment().format('M/D');
    }
  },
  methods: {
    async logout() {
      try {
        this.error = await this.$store.dispatch("logout");
      } catch (error) {
        console.log(error);
      }
    },
  }
}
</script>
