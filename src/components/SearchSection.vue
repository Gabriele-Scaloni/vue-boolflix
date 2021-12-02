<template>
    <div class="container">
        <form action="">
            <input type="text" placeholder="search your film"
            @change="$emit('cambiafilm', filmscelto)"
            v-model.trim="text">
            <button @click.prevent="textSearched"> search </button>
        </form>
    </div>

    <div>
        <Films v-for="film in filtraFilm"
        :key="film.id"
        :details="film"/>
    </div>
 
</template>

<script>

import axios from "axios";
import Films from '@/components/Films.vue';

export default {
  name: 'SearchSection',
  components: {
        Films
},
data() {
    return {
        listfilms: [],
        text:"",
        searchText: "",
    }
},
    created() {  //hook come mounted ma crea la struttura un pò prima rispetto al mounted
        this.getFilms
    },
    computed:{
        filtraFilm() {
            if(this.searchText === ""){
            return this.listfilms;
        }
            return this.listfilms.filter((element) => {
                return element.title.toLowerCase().includes(this.searchText.toLowerCase());
            })
        }
    },
    methods: {
        getFilms() {
            /* chiamo axios qui con il get chiamo l'api e poi con il then  che mi fa tornare l'oggetto*/
            axios
            .get("https://api.themoviedb.org/3/movie/550?api_key=5f2a64604e3748200cd6be6490a5e8b8")
            .then((result) => {
                this.listfilms = result.data;
            }) 
       },
        textSearched() {
            this.searchtext = this.text;
        }
   }

    
}
</script>

<style lang="scss">
.container {
    background-color: black;
    width: 100%;
    height: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>