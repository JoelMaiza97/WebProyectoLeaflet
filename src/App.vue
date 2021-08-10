<template>
  <div id="app">
    <l-map :zoom="zoom" :center="center">
      <l-tile-layer
        :url="osmUrl"
        :attribution="attribution"/>
      <l-routing-machine :waypoints="waypoints"/>
    </l-map>
  </div>
</template>

<script>
import { LMap, LTileLayer } from 'vue2-leaflet'
import LRoutingMachine from './components/LRoutingMachine'

const attribution = '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
const osmUrl = 'http://{s}.tile.osm.org/{z}/{x}/{y}.png'

export default {
  components: { LMap, LTileLayer, LRoutingMachine },
  data () {
    return {
      zoom: 6,
      center: { lat: -1.261285, lng: -78.632436 },
      osmUrl,
      attribution,
      waypoints: [
        L.latLng(-1.260942, -78.613523),
        L.latLng(-1.259775, -78.623854),
        L.latLng(-1.252601, -78.632975),
        L.latLng(-1.241757, -78.626915)
      ],
      language: 'es',
      routeWhileDragging: false
    }
  }
}

</script>

<style>
@import "../node_modules/leaflet/dist/leaflet.css";

html, body, #app {
  height: 100%;
  margin: 0;
}
</style>