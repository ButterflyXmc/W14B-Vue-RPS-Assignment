<template>
  <div>
    <main>
      <h1>LOGIN</h1>
      <h3>TO PLAY!</h3>

      <!-- user's email : eve.holt@reqres.in -->
      <label for="email"> Email </label>
      <input type="text" name="email" id="email" />
      <!-- user's pass : cityslicka -->
      <label for="password"> Password </label>
      <input type="text" name="email" id="pass" />
      <!-- when the user hit's submit, they'll be taken to the game page -->
      <button @click="login">Submit</button>
    </main>

    <div>
      <img
        src="https://media.baamboozle.com/uploads/images/164396/1637136389_114886_gif-url.gif"
        alt="gif"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import router from "@/router";
import cookies from "vue-cookies";

export default {
  name: "LoginPage",
  //creating a function for the user to login with the email and password thru the api
  methods: {
    login() {
      axios
        .request({
          url: "https://reqres.in/api/login",
          method: "POST",
          data: {
            email: document.getElementById(`email`).value,
            password: document.getElementById(`pass`).value,
          },
        })
        .then((response) => {
          console.log(response);
          //this will direct them to the game page with the path that I declared in index.js
          router.push("/game-page");
          //creating a cookie for when the user logs in -> the value's gonna be the token form the api
          cookies.set(`loginToken`, response.data.token);
        })

        // if the email or password is incorrect, an alert will pop up for the user
        .catch((error) => {
          this.error = error;
          this.error = alert("Incorrect email or password");
        });
    },
  },
  data() {
    return {
      error: "",
    };
  },
};
</script>

<style scoped>
img {
  height: 100vh;
  width: 45vw;
  margin-right: 55%;
}
</style>