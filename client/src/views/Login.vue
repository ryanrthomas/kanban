<template>
  <div class="container-fluid">
    <div class="login">
      <!-- <router-link to="/"><button class="btn m-3 btn-primary shadow">
          Go to boards view</button></router-link> -->
      <!-- <router-link to="/board/:boardId"><button class="btn m-3 btn-primary shadow">
          Go to board view</button></router-link> -->
      <form v-if="loginForm" @submit.prevent="loginUser" class="m-4">
        <div class="form-group text-left">
          <label>Email:</label>
          <input class="form-control shadow" type="email" v-model="creds.email" placeholder="Email...">
        </div>
        <div class="form-group text-left">
          <label>Password:</label>
          <input class="form-control shadow" type="password" v-model="creds.password" placeholder="Password...">
        </div>
        <button class="btn btn-primary shadow" type="submit">Login</button>
      </form>
      <form v-else @submit.prevent="register">
        <div class="form-group text-left">
          <label>Enter your name:</label>
          <input class="form-control shadow" type="text" v-model="newUser.name" placeholder="Name...">
        </div>
        <div class="form-group text-left">
          <label>Enter your email:</label>
          <input class="form-control shadow" type="email" v-model="newUser.email" placeholder="Email...">
        </div>
        <div class="form-group text-left">
          <label>Create a password:</label>
          <input class="form-control shadow" type="password" v-model="newUser.password" placeholder="Password...">
        </div>
        <button class="btn btn-primary shadow" type="submit">Create Account</button>
      </form>
      <div class="action" @click="loginForm = !loginForm">
        <p v-if="loginForm">No account? Click here to register</p>
        <p v-else>Already have an account? Click here to login</p>
      </div>
    </div>
  </div>
</template>

<script>
  import router from '@/router.js'
  export default {
    name: "login",
    data() {
      return {
        loginForm: true,
        creds: {
          email: "",
          password: ""
        },
        newUser: {
          email: "",
          password: "",
          name: ""
        }
      };
    },
    methods: {
      register() {
        this.$store.dispatch("register", this.newUser);
      },
      loginUser() {
        this.$store.dispatch("login", this.creds);
      }
    }
  };
</script>

<style>
  .action {
    cursor: pointer;
  }
</style>