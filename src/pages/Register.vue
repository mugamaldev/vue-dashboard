<template>
  <div class="auth">
    <h2>Register</h2>

    <form @submit.prevent="register">
      <input v-model="name" placeholder="Name" />

      <input v-model="email" placeholder="Email" />

      <input v-model="password" type="password" placeholder="Password" />

      <input v-model="password_confirmation" type="password" placeholder="Confirm Password" />

      <button>Register</button>
    </form>

    <p>
      Already have account? <router-link to="/login">Login</router-link>
    </p>
  </div>
</template>

<script>
import api from '../api/axios'

export default {
  data() {
    return {
      name: "",
      email: "",
      password: "",
      password_confirmation: "",
    }
  },

  methods: {
    async register() {
      try {
        await api.post("/auth/register", {
          name: this.name,
          email: this.email,
          password: this.password,
          password_confirmation: this.password_confirmation, // مهم جداً
        });

        this.$router.push("/login");
      } catch (e) {
        console.log("REG ERROR:", e.response.data);
        alert("Register failed: " + JSON.stringify(e.response.data));
      }
    }
  }
}
</script>
