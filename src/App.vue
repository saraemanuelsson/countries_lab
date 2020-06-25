<template>
  <div id="app">
    <h1>Countries</h1>
    <div class="main-container">
      <countries-dropdown :countries="countries" :selectedCountry="selectedCountry"></countries-dropdown>
      <hr>
      <country-detail :country="selectedCountry"></country-detail>
    </div>
  </div>
</template>

<script>
import Dropdown from './components/Dropdown.vue'
import CountryDetail from './components/CountryDetail.vue'
import { eventBus } from './main.js'


export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on("country-selected", (country) => {
      this.selectedCountry = country
    })
  },
  components: {
    "countries-dropdown": Dropdown,
    "country-detail": CountryDetail
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
