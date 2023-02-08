<script>
import AppSearch from "./AppSearch.vue";
import { store } from "../store";

export default {
  name: "AppHeader",
  components: { AppSearch },
  data() {
    return {
      store,
    };
  },

  methods: {
    testMess(parametro, num) {
      console.log("hey", parametro, num);
    },

    incrementa() {
      this.store.counter++;
    },
  },
};
</script>

<template>
  <AppSearch message="ciao" @eventodalfiglio="testMess" />
  <h2>{{ store.counter }}</h2>
  <button @click="incrementa">btn header</button>
</template>

<style scoped></style>
