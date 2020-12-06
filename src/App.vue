<template>
  <div id="app">
    <UserProfile />
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";

export default {
  name: "App",
  components: {
    UserProfile,
  },
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100%;
  margin: 0;
  padding: 0;
  background-color: #f3f5fa;
}
</style>
