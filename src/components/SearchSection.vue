<template>

    <form action="">
        <input type="text" placeholder="search your film"
        @search="$emit('cambiafilm', filmscelto)"
        v-model.trim="textSearched">
        <button @click.prevent="textSearched"> search </button>
    </form>

</template>

<script>

export default {
  name: 'SearchSection',
   data() {
       return {
            textSearched:"",

       }
   },
}       


</script>

<style lang="scss">

</style>