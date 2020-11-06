<template>
  <div>
    <label v-for="country of countries" :key="country">
      <input type="checkbox" :value="country" :name="country" v-model="selectedCountries"/>
      {{country}}
    </label>
  </div>
</template>

<script>
export default {
  name: "CheckBoxes",
  data() {
    return {
      countries: ['Sweden', 'Spain', 'UK', 'USA', 'Germany', 'Japan', 'Australia'],
      positions: {
        Sweden: {lat: 60.128161, lng: 18.643501},
        Spain: {lat: 40.463667, lng: -3.74922},
        UK: {lat: 55.378051, lng: -3.435973},
        USA: {lat: 37.09024, lng: -95.712891},
        Germany: {lat: 51.165691, lng: 10.451526},
        Japan: {lat: 36.204824, lng: 138.252924},
        Australia: {lat: -25.274398, lng: 133.775136}

      },
      selectedCountries: []
    }
  },
  computed :{
    currentPositions(){
      return this.selectedCountries.map(country=> this.positions[country])
    }
  },
  watch:{
    selectedCountries(){
      this.$emit('updateZooming',this.currentPositions);
    }
  }
}
</script>

<style scoped>

</style>