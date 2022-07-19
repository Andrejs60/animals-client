<template>
  <NavBar />
  <router-view />
</template>

<script>
import NavBar from "../src/components/navigation/NavBar.vue";

export default {
  name: "App",
  components: { NavBar },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

body {
  background: #ebf9fc;
  padding: 0;
  margin: 0;
}

* {
  box-sizing: border-box;
}
</style>
