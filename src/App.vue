<template>
  <div id="app">
      <bracket></bracket>
  </div>
</template>

<script>
import bracket from "./components/bracket"
export default {
  name: 'app',
  components: {
      bracket,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
