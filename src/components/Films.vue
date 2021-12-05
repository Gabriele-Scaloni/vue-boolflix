<template>
  <div class="container-cards">
    <div class="film-card">
      <img :src=" `https://image.tmdb.org/t/p/w154${poster_path}` " alt="film" />
      <h3>Titolo: {{ details.title }}</h3>
      <p>Titolo originale: {{ details.original_title || details.original_name }}</p>
      <p>Lingua originale : {{ details.original_language }}</p>
      <div>
        <span> Lingua:</span>
        <img class="flag" :src="FlagLanguage()" alt= "" />
      </div>
      <ul>
        <li v-for="index in 5" :key="index" class="star" :class="star(index, vote())">
          <i class="fas fa-star"></i>
          </li>
      </ul>

    </div>
  </div>
</template>
<script>
/* font awesome, prima si installa nel terminale e poi si importa,
 controllare versione nel json, come axios in App.vue */
import '@fortawesome/fontawesome-free/css/all.css'
import '@fortawesome/fontawesome-free/js/all.js'

export default {
  name: "Films",
  props: {
    details: Object,
  },


  methods: {
    FlagLanguage() {
      if (this.details.original_language === "it") {
        return "https://m.media-amazon.com/images/I/31g0+P5xoML._AC_SX466_.jpg";
      } else if (this.details.original_language === "en") {
        return "https://m.media-amazon.com/images/I/41+fJSCwMJL._AC_.jpg";
      } else {
        return "https://www.prestashop.com/sites/default/files/styles/blog_750x320/public/blog/2019/10/banner_error_404.jpg?itok=eAS4swln"
      }
    },
    star(index, val) {

      if (index <= val) {
        return "active";
      }
    },
    vote(){ 
        return Math.round(this.details.vote_average / 2);
    },
 },
}; 
</script>

<style lang="scss">
.container-cards {
  float: left;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
}
.film-card {
  width: 150px;
  height: 300px;
  float: left;
  background-color: rgb(105, 105, 105);
  margin: 10px 5px;
  padding: 10px 5px;
}
.flag {
  width: 30px;
  height: 20px;
}
li {
  display:inline;
}
.active{ 
  color: gold;
}

</style>