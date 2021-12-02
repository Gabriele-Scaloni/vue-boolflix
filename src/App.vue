<template>
<div id="app">
  <SearchSection @cambiafilm="filmscelti"/>
</div>

</template>

<script>

import SearchSection from './components/SearchSection.vue';

export default {
  name: "App",
  components: {
    SearchSection,
},
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>