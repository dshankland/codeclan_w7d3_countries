<template lang="html">
  <div>
    <p>The Countries Dropdown</p>
    <select v-on:change="handleChange" v-model="selected">
      <option selected>Select Country</option>
      <!-- v-model in the select is the relevant part, v-bind:value would be for a form -->
      <option v-for="(country, index) in countries" v-bind:value="country" >{{ country.name }}</option>
    </select>
      <!-- <countries-list-item v-for="(country, index) in countries" :country="country" :key="index">{{country.name}}</countries-list-item> -->
  </div>

</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'countries-dropdown',
  props: ['countries'],
  methods: {
  handleChange: function(){
    console.log(this.selected);
    eventBus.$emit('country-selected', this.selected)
  }
}
}
</script>

<style lang="css" scoped>
</style>
