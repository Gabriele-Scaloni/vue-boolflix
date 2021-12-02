<template>
  <div id="app">
    <MyHeader @search="handleSearch" />
    <Films v-for="film in listfilms"
        :key="film.id"
        :details="film"/>

    <Series v-for="serie in listseries"
    :key="serie.id"
    :particolari="serie"/>
  </div>
</template>

<script>
import axios from "axios";
import MyHeader from "./components/MyHeader.vue";
import Films from '@/components/Films.vue';
import Series from '@/components/Series.vue';

export default {
  name: "App",
  components: {
    MyHeader,
    Films,
    Series,
  },
  data() {
    return {
      apiUrlFilms:"https://api.themoviedb.org/3/search/movie/?api_key=5f2a64604e3748200cd6be6490a5e8b8&query=",
      apiUrlSeries: "https://api.themoviedb.org/3/search/tv/?api_key=5f2a64604e3748200cd6be6490a5e8b8&query=",
      listfilms: [],
      listseries: [],
      searchText: "",
    }
  },
  methods: {
    handleSearch(searchMovie) {
      this.searchText = searchMovie;
      this.getFilms();
      this.getSeries();
    },
    getFilms() {
      /* chiamo axios qui con il get chiamo l'api e poi con il then  che mi fa tornare l'oggetto*/
      axios.get(this.apiUrlFilms+this.searchText).then((result) => {
        this.listfilms = result.data.results;
      });
    },
    getSeries() {//aggiungo all'API searchText
      axios.get(this.apiUrlSeries+this.searchText).then((result) => {
        this.listSeries = result.data.results;
      });
    },
  
  },
};
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