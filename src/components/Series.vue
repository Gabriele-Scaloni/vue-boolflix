<template>

    <div class="container-cards-serie">
        <div class="serie-card">
            <!-- <img :src="details.poster_path" alt="serie" /> -->
            <h3>Titolo: {{ particolari.name }}</h3>
            <p>Titolo originale: {{ particolari.original_name }}</p>
            <!-- <p>Lingua originale : {{ particolari.original_language }}</p> -->
            <div>
                <span> Lingua:</span>
                <img class="flag" :src="FlagLanguage()" alt="">
            </div>
            <p>Voto: {{ particolari.vote_average }}</p>
        </div>
    </div>

</template>

<script>
export default {
  name: "Series",
  props: {
    particolari: Object,
  },
};
</script>

<style lang="scss">
</style>