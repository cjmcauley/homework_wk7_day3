<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <country-list :countries='countries'></country-list>
      <country-detail :country='selectedCountry'></country-detail>
    </div>

  </div>
</template>

<script>
import { eventBus } from './main.js';
import CountryList from './components/CountryList.vue';
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
    .then(result => result.json())
    .then(countries =>this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "country-list": CountryList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>
