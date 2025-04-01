<template>
  <TheNav></TheNav>
  <TheView></TheView>
</template>

<script>

import TheNav from "../components/TheNav.vue";
import TheView from "../components/TheView.vue";
import { ref,watch } from 'vue';

export default {
  components: {
    TheNav,
    TheView,
  },

  setup () { 
    return {
      // data
      // computed
      // methods
    };
}
}
</script>

<style lang="scss" scoped>

</style>