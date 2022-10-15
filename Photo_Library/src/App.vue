<template>
  <v-app>
    <Nav_app />
    <router-view />
  </v-app>
</template>

<script>
import Nav_app from "@/components/Nav_app.vue";

export default {
  name: 'App',
  components: {
    Nav_app
  }
};
</script>
