<template>
  <div id="map"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";
export default {
  name: "MapaComponent",
  data: () => ({
    icon: undefined,
    map: undefined,
  }),
  mounted() {
    this.setupMap();
  },
  methods: {
    setupMap() {
      //Fazendo o ícone
      this.icon = L.icon({
        iconUrl: "../assets/navegacao-gps.png",
        iconSize: [38, 95],
        shadowSize: [50, 64],
        iconAnchor: [22, 94],
        popupAnchor: [-3, -76],
      });
      this.map = L.map("map").setView([-0.11533291437044707, -67.09336742717267], 13);
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 19,
        attribution: "© OpenStreetMap",
      }).addTo(this.map);
    },
  },
};
</script>

<style scoped>
#map {
  width: 80vw;
  height: 100vh;
}
</style>
