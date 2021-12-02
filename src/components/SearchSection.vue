<template>

    <form action="">
        <input type="text" placeholder="search your film"
        v-model.trim="textSearched">
        <button @click.prevent="$emit('cambiafilm', textSearched)"> search </button>
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