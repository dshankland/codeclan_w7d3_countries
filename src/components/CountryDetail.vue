<template lang="html">
  <div v-if="country">
    <h3>{{country.name}}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <img v-bind:src="country.flag" width=300 height=200>
    <p>Languages :-</p>
    <ul>
      <!-- could and probably should abstract this further into another component -->
      <li v-for="(language, index) in country.languages" :language="language" :key="index">{{language.name}}</li>
    </ul>

  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
