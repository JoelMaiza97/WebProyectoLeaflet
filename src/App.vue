<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      <router-link to="/LRoutingMachine">Map</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
@import "../node_modules/leaflet/dist/leaflet.css";

html, body, #app {
  height: 100%;
  margin: 0;
}
</style>