<template>
  <div class="main">
    <h1>Sign In!</h1>
    <form @submit.prevent="pushSignin">
      <div class="form-control">
        <label for="userName">User Name</label>
        <input type="text" name="userName" id="userName" v-model="userName" />
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
      <button type="submit">Sign In</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userName: "",
      password: "",
    };
  },
  methods: {
      pushSignin() {
          fetch('https://vue-shop-e7ce5.firebaseio.com/users.json', {
              method: 'POST',
              headers: {
                  'Content-Type': 'applications/json',
              },
              body: JSON.stringify({
                  userName: this.userName,
                  password: this.password
              })
          });
      }
  }
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
    background-color: #5CDB95;
    padding: 10px 5px;
    width: 100px;
    height: 45px;
    color: #EDF5E1;
    font-size: 20px;
    border-style: none;
    cursor: pointer;
    border-radius: 10px;
    text-decoration: none;
    margin-left: 20px;
    box-shadow: 0 2px 8px #032241;
}
</style>