<template lang="html">
  <div>
    <p>The Countries Dropdown</p>
    <select v-on:change="handleChange" v-model="selected">
      <option selected>Select Country</option>
      <!-- v-model in the select is the relevant part, v-bind:value would be for a form -->
      <option v-for="(country, index) in countries" v-bind:value="country" >{{ country.name }}</option>
    </select>
      <!-- <countries-list-item v-for="(country, index) in countries" :country="country" :key="index">{{country.name}}</countries-list-item> -->

      <div class="search-wrapper">
        <input class="search" type="text" name="search" v-model="search" placeholder="Search countries...">
      </div>

  </div>

</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'countries-dropdown',
  data(){
    return {
      selected: null,
      search: ""
    };
  },
  props: ['countries'],
  methods: {
  handleChange: function(){
    // console.log(this.selected);
    eventBus.$emit('country-selected', this.selected)
  }
},
computed: {
  searchedCountries: function () {
    this.selected = this.countries.filter((country) => {
      return country.name.match(this.search);
    });
  },
}
}
</script>

<style lang="css" scoped>
</style>
