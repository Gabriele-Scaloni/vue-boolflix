<template>
<div id="app">
  <MyHeader @cambiafilm="filmscelti"/>

    
</div>

</template>

<script>

import MyHeader from './components/MyHeader.vue';

export default {
  name: "App",
  components: {
    MyHeader,
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