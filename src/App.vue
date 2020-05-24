/* eslint-disable vue/no-unused-components */ /* eslint-disable
vue/no-unused-components */ /* eslint-disable vue/no-unused-components */
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="50px" />
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
import Skills from "./components/Skills.vue";

export default {
  name: "app",
  components: {
    // eslint-disable-next-line vue/no-unused-components
    Skills
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

body {
  background-color: #eeeeee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
}
nav {
  padding: 20px 20px 20px 0;
}

nav a {
  padding: 10px;
  text-decoration: none;
  background: #fff;
  border-radius: 3px;
  color: rgb(0, 110, 255);
  font-weight: bold;
  margin-right: 15px;
}

button {
  padding: 10px;
  display: none;
  background: #eee;
  color: rgb(0, 110, 255);
  font-weight: bold;
  margin: 15px 15px 15px 0;
  border: none;
  cursor: pointer;
  display: inline;
}

button:hover {
  background: #cccccc;
}

body,
html {
  margin: 0;
  height: 100%;
  padding: 10px;
}

@media (min-width: 320px) {
  #app {
    width: 100%;
    font-size: 0.8em;
  }
}

@media (min-width: 961px) {
  #app {
    width: 50%;
  }
}
</style>
