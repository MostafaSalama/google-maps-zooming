<template>
<div class="container">
  <div class="map" ref="map">

  </div>
</div>
</template>

<script>
import {Loader} from "@googlemaps/js-api-loader"

export default {
  name: "GoogleMapContainer",
  data() {
    return {
      map: null,

    }
  },
  mounted() {
    const loader = new Loader({
      apiKey: "AIzaSyB94wtYbbU7JEsO8XIF9sJpMTAlBsBVti0",
      version: "weekly",
    });
    loader.load().then(() => {
      this.map = new google.maps.Map(this.$refs.map, {
        center: {lat: -34.397, lng: 150.644},
        zoom: 10,
      });
    });
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.map {
  width: 80vw;
  height: 400px;
}
</style>