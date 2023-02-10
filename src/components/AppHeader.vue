<script>
import { store } from "../store";

export default {
  name: "AppHeader",

  data() {
    return {
      store,
    };
  },

  methods: {},
};
</script>

<template>
  <div class="containerHeader">
    <div class="logo">
      <img src="../img/Logonetflix.png" />
    </div>
    <div class="barraInputButton">
      <input
        class="inputCerca"
        type="text"
        v-model="store.searchText"
        placeholder="cerca"
      />

      <img class="iconaLente" src="../img/49116.png" />

      <button class="btnInvia" @click="$emit('performSearch')">Invia</button>
    </div>
  </div>
</template>

<style scoped></style>
