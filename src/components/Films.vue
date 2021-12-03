<template>
  <div class="container-cards">
    <div class="film-card">
      <img :src=" `https://image.tmdb.org/t/p/w154$ {{details.poster_path}}` " alt="film" />
      <h3>Titolo: {{ details.title }}</h3>
      <p>Titolo originale: {{ details.original_title }}</p>
      <p>Lingua originale : {{ details.original_language }}</p>
      <div>
        <span> Lingua:</span>
        <img class="flag" :src="FlagLanguage()" alt= "" />
      </div>
      <ul>
        <li>Voto: {{ vote() }} </li>
        <li class="star"><i class="fas fa-star" v-if="vote"></i></li>
        <li class="star"><i class="fas fa-star"></i></li>
        <li class="star"><i class="fas fa-star"></i></li>
        <li class="star"><i class="fas fa-star"></i></li>
        <li class="star"><i class="fas fa-star"></i></li>
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
    vote(){ 
        if (this.details.vote_average === 0) {
        return 0
      } else if ( this.details.vote_average <= 2 != 0) {
        return 1 
      } else if ( this.details.vote_average <= 4) {
        return 2 
      } else if ( this.details.vote_average <= 6) {
        return 3 
      } else if ( this.details.vote_average <= 8) {
        return 4
      } else if( this.details.vote_average <= 10) {
        return 5
      }
    },
    getImg () {

    }

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
.star {
  color: gold;
}
</style>