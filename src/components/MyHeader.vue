<template>
    <div>
        <div class="container">
            <SearchSection @cambiafilm="textSearched"/>
        </div>

        <Films v-for="film in filtraFilm"
        :key="film.id"
        :details="film"/>

    </div>
</template>

<script>
 
import axios from "axios";
import Films from '@/components/Films.vue';
import SearchSection from '@/components/SearchSection.vue';

export default {
  name: 'MyHeader',
  components: {
    Films,
    SearchSection
},
data() {
    return {
        apiUrl:"https://api.themoviedb.org/3/movie/550?api_key=5f2a64604e3748200cd6be6490a5e8b8",
        listfilms: [],
        searchText: "",
        query : ""  /* &title= ? */
    }
}, 
    created() {  //hook come mounted ma crea la struttura un pò prima rispetto al mounted
        this.getFilms();
    },
    methods: {
        getFilms() {
            /* chiamo axios qui con il get chiamo l'api e poi con il then  che mi fa tornare l'oggetto*/
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.listfilms = result.data.result;
            }) 
        },
        /*    textSearched(textWritten) {
            this.searchtext = textWritten;
        } */
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