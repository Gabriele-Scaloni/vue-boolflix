<template>
  <div class="filmcard">
    <!-- <img :src="details.poster_path" alt="film" /> -->
    <h3>Titolo : {{ details.title }}</h3>
    <p>Titolo originale: {{ details.original_title }}</p>
    <!-- <p>Lingua originale : {{ details.original_language }}</p> -->
    <div><span> Lingua :<img class="flag" :src="FlagLanguage()" alt=""></span></div>
    <p>Voto : {{ details.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Films",
  props: {
    details: Object,
  },
  /* const this.details.original_language = lingua; */
  methods: {
    FlagLanguage() {
      if (this.details.original_language === "it") {
        return "https://m.media-amazon.com/images/I/31g0+P5xoML._AC_SX466_.jpg";
      } else if (this.details.original_language === "en") {
        return "https://m.media-amazon.com/images/I/41+fJSCwMJL._AC_.jpg";
      }
    },
  },
};
</script>

<style lang="scss">
.flag {
    width: 30px;
    height: 20px;
}
</style>