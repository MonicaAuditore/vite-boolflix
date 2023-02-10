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
      <img class="iconaLente" src="../img/49116.png" />
      <button @click="$emit('performSearch')">Invia</button>
    </div>
  </div>
</template>

<style scoped>
::placeholder {
  color: #141414;
}

input {
  padding: 10px;
  padding-left: 45px;
  margin-right: 20px;
  border-radius: 50px;
  position: relative;
  background-color: transparent;
  width: 68px;
  transition: all 2s;

  border: none;
}

.barraInputButton:hover textarea {
  color: #ffffff;
}

.barraInputButton:hover ::placeholder {
  color: rgb(255, 255, 255);
  transition: all 2s;
}

textarea:focus,
input:focus {
  color: #ffffff;
}

.barraInputButton:hover input {
  width: 250px;
  transition: all 2s;
  border: 1px solid #727272;
}

.barraInputButton:hover .iconaLente {
  right: 387px;
  transition: all 2s;
}

.iconaLente {
  width: 23px;
  position: absolute;
  right: 200px;
  top: 33px;
  transition: all 2s;
}

button {
  padding: 15px 40px;
  border-radius: 50px;
  cursor: pointer;

  background-color: #f0f8ff00;
  border: 0.5px solid white;
  color: white;
}

.containerHeader {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 45px;
  background-color: #141414d1;

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
