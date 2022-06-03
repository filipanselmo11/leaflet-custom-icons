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
      this.map = L.map("map").setView([-3.042602743486333, -59.95165651808512], 13);
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        maxZoom: 19,
        attribution: "© OpenStreetMap",
      }).addTo(this.map);
      L.marker([-0.13567335749927611, -67.07951344157546], { icon: this.icon }).addTo(
        this.map
      );
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
