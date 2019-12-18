<template>
  <div>
  <h1>Countries</h1>
    <div class="main-container">
      <countries-list :countries='countries'></countries-list>
      <country-details :country='selectedCountry'></country-details>
    </div>
  </div>
</template>

<script>
  import CountriesList from './components/CountriesList.vue';
  import { eventBus } from './main.js';
  import CountryDetail from './components/CountryDetail.vue';

  export default {
    name: 'app',
    data(){
      return {
        countries: [],
        selectedCountry: null
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
      "countries-list": CountriesList,
      "country-details": CountryDetail

    }
  }
</script>

<style>
.main-container {
    display: flex;
    justify-content: center;
  }
</style>
