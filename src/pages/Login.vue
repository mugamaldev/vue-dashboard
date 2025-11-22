<template>
  <div class="auth">
    <h2>Login</h2>
    <form @submit.prevent="login">

      <input v-model="email" placeholder="Email">
      <input v-model="password" type="password" placeholder="Password">

      <button>Login</button>
    </form>

    <p>
      No account? <router-link to="/register">Register</router-link>
    </p>
  </div>
</template>

<script>
import api from '../api/axios'

export default {
  data() {
    return {
      email: "",
      password: "",
    }
  },

  methods: {
    async login() {
      const res = await api.post("/auth/login", {
        email: this.email,
        password: this.password,
      });

      localStorage.setItem("token", res.data.access_token);
      this.$router.push("/dashboard");
    }
  }
}
</script>
