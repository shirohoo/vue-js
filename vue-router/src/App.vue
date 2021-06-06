<template>
  <router-view />
</template>

<script>
import Vuetify from "vuetify";

export default {
  name   : 'App',
  vuetify: new Vuetify(),
  props  : {
    source: String,
  },
  data   : () => ({
    drawer: null,
  }),
};
</script>
