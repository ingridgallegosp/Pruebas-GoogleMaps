<template>
  <GoogleMapLoader :mapConfig="mapConfig" apiKey="yourApiKey">
    <template slot-scope="{ google, map }">
      {{ map }}
      {{ google }}
    </template>
  </GoogleMapLoader>
</template>

<script setup>
import GoogleMapLoader from "./GoogleMapLoader.vue";
//import { mapSettings } from "./constants/mapSettings";

export default {
  components: {
    GoogleMapLoader,
  },
  computed: {
    mapConfig() {
      return {
        ...mapSettings,
        center: { lat: 0, lng: 0 },
      };
    },
  },
};
</script>
