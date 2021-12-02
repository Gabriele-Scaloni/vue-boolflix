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
  }
}

</script>

<style lang="scss">

</style>