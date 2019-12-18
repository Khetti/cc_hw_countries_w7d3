<template>
  <div id="app">

    <h1>Countries</h1>
<div class="main-container">


    <countries-list :countries='countries'></countries-list>
    <country-details :country='selectedCountry'></country-details>
</div>
  </div>
</template>

<script>
import countriesList from './components/countriesList.vue';
import { eventBus } from './main.js';
import countryDetails from './components/countryDetails.vue';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: {}
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries => this.countries = countries)


    console.log('listening for country-selected');
    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country
    })
  },
  components: {
    "countries-list": countriesList,
    "country-details": countryDetails

  }
}
</script>

<style>
.main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
