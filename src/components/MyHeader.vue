<template>
  <div>
    <div class="container-form">
      <form action="">
        <input
          type="text"
          placeholder="search your film"
          v-model.trim="textSearched"
        />
        <button @click.prevent="$emit('search', textSearched)">search</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyHeader",
  data() {
    return {
      textSearched: "",
    };
  },
};
</script>

<style lang="scss">
.container-form {
  background-color: black;
  width: 100%;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>