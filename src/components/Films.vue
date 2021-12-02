<template>

    <div>
        <img :src="details.poster_path" alt="film">
        <p>{{details.title}}</p>
        <p>{{details.original_title}}</p>
        <p>{{details.original_language}}</p>
        <p>{{details.vote_average}}</p>
    </div>

</template>

<script>

export default {
  name: 'Films',
  props: {
    details: Object,
  },
    /* const this.details.original_language = lingua; */
methods :{
    FlagLanguage() {
        if ( this.details.original_language === 'it'){
            return "https://m.media-amazon.com/images/I/31g0+P5xoML._AC_SX466_.jpg"
        } else if ( this.details.original_language === 'en'){
            return "https://m.media-amazon.com/images/I/41+fJSCwMJL._AC_.jpg"
        }
    }
}
}
</script>

<style lang="scss">

</style>