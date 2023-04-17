<template>
  <div>
    <div class="google-map" ref="googleMap"></div>
    <template v-if="Boolean(this.google) && Boolean(this.map)">
      <slot :google="google" :map="map"> </slot>
    </template>
  </div>
</template>

<script>
import GoogleMapsApiLoader from "google-maps-api-loader"; //para que funcione falta acceder a la API y las credenciales

export default {
  props: {
    mapConfig: Object,
    apiKey: String,
  },

  data() {
    return {
      google: null,
      map: null,
    };
  },

  async mounted() {
    const googleMapApi = await GoogleMapsApiLoader({
      apiKey: this.apiKey,
    });
    this.google = googleMapApi;
    this.initializeMap();
  },

  methods: {
    initializeMap() {
      const mapContainer = this.$refs.googleMap;
      this.map = new this.google.maps.Map(mapContainer, this.mapConfig);
    },
  },
};
</script>
