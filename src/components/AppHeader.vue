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
      <input type="text" v-model="store.searchText" placeholder="cerca" />
      <button @click="$emit('performSearch')">Cerca</button>
    </div>
  </div>
</template>

<style scoped>
.barraInputButton input {
  margin-right: 20px;
}

input {
  padding: 10px;
  padding-right: 60px;
  border-radius: 50px;
}

button {
  padding: 15px 40px;
  border-radius: 50px;
}

.containerHeader {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  background-color: #141414;

  position: fixed;
  width: 100%;
  z-index: 200;
}

.logo {
  width: 120px;
}

.logo img {
  width: 100%;
}
</style>
