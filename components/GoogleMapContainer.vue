<template>
  <div class="container">
    <div class="map" ref="map">

    </div>
    <div class="countries-container">
      <h2>Choose Countries</h2>
      <CheckBoxes @updateZooming="updateZooming"/>
    </div>
  </div>
</template>

<script>
import {Loader} from "@googlemaps/js-api-loader"
import CheckBoxes from "~/components/CheckBoxes";

export default {
  name: "GoogleMapContainer",
  components: {CheckBoxes},
  data() {
    return {
      map: null,
      markers: [],
      initialCenter: {lat: -34.397, lng: 150.644}
    }
  },
  mounted() {
    const loader = new Loader({
      apiKey: "AIzaSyB94wtYbbU7JEsO8XIF9sJpMTAlBsBVti0",
      version: "weekly",
    });
    loader.load().then(() => {
      this.map = new google.maps.Map(this.$refs.map, {
        center: this.initialCenter,
        zoom: 10,
      });
    });
  },
  methods: {
    updateZooming(positions) {
      this.clearMarkers();
      if (!positions.length) {
        this.map.setCenter(this.initialCenter);
        return  ;
      }
      this.createMarkers(positions) ;
      if (positions.length === 1) {
        this.map.setCenter(positions[0]);
        return  ;
      }
      const bounds = new google.maps.LatLngBounds();
      positions.forEach(p=>{
        bounds.extend(p);
      });
      this.map.fitBounds(bounds);
    },
    clearMarkers() {
      this.markers.forEach(marker => marker.setMap(null));
    },
    /**
     * array of positions to create markers from them
     * @param positions {Array}
     */
    createMarkers(positions) {
      positions.forEach(p => {
        const marker = new google.maps.Marker({
          position: p,
          map: this.map
        });
        this.markers.push(marker)
      })
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.map {
  width: 80vw;
  height: 400px;
}

.countries-container {
  margin-top: 20px;
}
</style>