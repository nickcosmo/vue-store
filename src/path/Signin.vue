<template>
  <div class="main">
    <h1>Sign In or Sign Up</h1>
    <form @submit.prevent="submitForm">
      <div class="form-control">
        <label for="email">Email</label>
        <input type="text" name="email" id="email" v-model="email" />
      </div>
      <div class="form-control">
        <label for="password">Password</label>
        <input
          type="password"
          name="password"
          id="password"
          v-model="password"
        />
      </div>
      <button type="submit" @click="submitType = 'signin'">Sign In</button>
      <button type="submit" @click="submitType = 'signup'">Sign Up</button>
      <p v-if="validated === false">Please complete the form</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      validated: true,
      isLoading: false,
      error: null,
      submitType: null
    };
  },
  methods: {
    checkForm() {
      if (this.email === "" || this.password === "") {
        this.validated = false;
      } else {
        this.validated = true;
      }
    },
    async submitForm() {
      this.checkForm();
      if (this.validated === false) {
        return;
      }

      this.isLoading = true;
      if (this.submitType === "signup") {
        try {
          await this.$store.dispatch("signup", {
            email: this.email,
            password: this.password,
          });
        } catch (err) {
          this.error = err.message || "authentication failed";
        }
        this.isLoading = false;
      } else if (this.submitType === "signin") {
        try {
          await this.$store.dispatch("login", {
            email: this.email,
            password: this.password,
          });
        } catch (err) {
          this.error = err.message || "authentication failed";
        }
        this.isLoading = false;
      }
    },
  },
};
</script>

<style scoped>
.main {
  box-shadow: 2px 2px 8px rgba(54, 54, 54, 0.26);
  background-color: #efefef;
  border: none;
  border-radius: 10px;
  text-align: center;
  width: 40%;
  margin: 80px auto;
  padding: 40px 60px;
}

.form-control {
  margin-top: 10px;
  width: 100%;
  font-size: 20px;
  margin: 10px 5px;
}

label,
input {
  border: none;
  border-radius: 4px;
  font-size: 20px;
  margin: 5px;
  padding: 3px;
  outline: none;
}

button {
  outline: none;
  display: inline-block;
  background-color: #5cdb95;
  padding: 10px 5px;
  height: 45px;
  color: #edf5e1;
  font-size: 20px;
  border-style: none;
  cursor: pointer;
  border-radius: 10px;
  text-decoration: none;
  margin-left: 20px;
  box-shadow: 0 2px 8px #032241;
}
</style>