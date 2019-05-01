<template lang="html">
  <div>
    <p>The Countries List</p>
    <ul>
      <countries-list-item v-for="(country, index) in countries" :country="country" :key="index">{{country.name}}</countries-list-item>
    </ul>
  </div>

</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "countries-list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>
