<script>
import AppSearch from "./AppSearch.vue";

export default {
  name: "AppHeader",
  components: { AppSearch },
  data() {
    return {};
  },

  methods: {
    testMess(parametro, num) {
      console.log("hey", parametro, num);
    },
  },
};
</script>

<template>
  <AppSearch message="ciao" @eventodalfiglio="testMess" />
</template>

<style scoped></style>
