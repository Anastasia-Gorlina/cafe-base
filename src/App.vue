<template>
    <div id="app"><Profile /><Cafe /></div>
</template>

<script>
import Profile from "./components/Profile.vue";
import Cafe from "./components/Cafe.vue"

export default {
  name: "App",
  components: { Profile, Cafe },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 50px;
}

.info > div:not {
  margin-bottom: 0.6em;
}
</style>