<template>
    <div class="container-cards">
        <div class="film-card">
            <!-- <img :src="details.poster_path" alt="film" /> -->
            <h3>Titolo: {{ details.title }}</h3>
            <p>Titolo originale: {{ details.original_title }}</p>
            <!-- <p>Lingua originale : {{ details.original_language }}</p> -->
            <div>
                <span> Lingua:</span>
                <img class="flag" :src="FlagLanguage()" alt="">
            </div>
            <p>Voto: {{ details.vote_average }}</p>
        </div>
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
.container-cards {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
}
.film-card {
    width: 150px;
    height: 300px;

    background-color: rgb(105, 105, 105);
    margin: 10px 5px;
}
.flag {
    width: 30px;
    height: 20px;
}
</style>