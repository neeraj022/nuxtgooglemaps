<template>
  <section class="container">
    <img src="../assets/img/logo.png" alt="Nuxt.js Logo" class="logo" />
    <h1 class="title">
      Universal Vue.js Application Framework
    </h1>
    <nuxt-link class="button" to="/about">
      About page
    </nuxt-link>

    <label>
          Das Label
          <gmap-autocomplete :value="description"
            @place_changed="setPlace">
          </gmap-autocomplete>
        </label>

  </section>
</template>

<script>
import * as VueGoogleMaps from 'vue2-google-maps'
import Vue from 'vue'

Vue.use(VueGoogleMaps, {
  load: {
    key: 'AIzaSyBzlLYISGjL_ovJwAehh6ydhB56fCCpPQw',
    libraries: 'places'
  }
})
export default {
    data () {
        return {
            description: 'India',
            latLng: {}
          }
        },
      methods:
      {
        setDescription (description) {
        this.description = description
      },
      setPlace (place) {
        this.latLng = {
          lat: place.geometry.location.lat(),
          lng: place.geometry.location.lng()
        }
      }
    }
}

</script>

<style scoped>
.title
{
  margin: 50px 0;
}
</style>
