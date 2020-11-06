<template>
  <div>
    <h1 class="title">
        Google Countries Zooming
      </h1>
    <GoogleMapContainer/>
  </div>
</template>

<script>
import GoogleMapContainer from "~/components/GoogleMapContainer";
export default {
  components: {GoogleMapContainer}
}
</script>

<style>

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 3rem;
  color: #35495e;
  letter-spacing: 1px;
  text-align: center;
}


</style>
