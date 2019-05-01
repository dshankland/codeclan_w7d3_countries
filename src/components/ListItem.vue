<template lang="html">
  <li v-on:click="handleClick">{{country.name}}</li>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'country-list-item',
  props: ['country'],
  methods: {
  handleClick: function(){
    // console.log(this.munro);
    eventBus.$emit('country-selected', this.country)
  }
}
}
</script>

<style lang="css" scoped>
</style>
