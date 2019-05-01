<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <countries-dropdown v-bind:countries='countries'></countries-dropdown>
      <countries-list v-bind:countries='countries'></countries-list>
      <country-detail :country='selectedCountry'></country-detail>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountriesDropdown from './components/CountriesDropdown.vue';
import CountryDetail from './components/CountryDetail.vue';
import { eventBus } from './main.js'

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  methods: {
    fetchCountries: function(){
      // request is a promise object
      fetch("https://restcountries.eu/rest/v2/all")
      .then(response => response.json())
      .then((data) => {
        // console.log(data);
        this.countries = data;
        // console.log(this.countries);
        // any subsequent dependant functions has to happen here
      });
    },
  },
  mounted(){
    // console.log('loaded');
    this.fetchCountries();
    // console.log(this.countries);
    eventBus.$on('country-selected', (country) => {
      // console.log('within $on', country);
      this.selectedCountry = country;
    });
},
  components: {
    'countries-list': CountriesList,
    'countries-dropdown': CountriesDropdown,
    'country-detail': CountryDetail
  }
}
</script>

<style lang="css" scoped>
.main-container {
  display: flex;
  justify-content: space-between;
}
</style>

