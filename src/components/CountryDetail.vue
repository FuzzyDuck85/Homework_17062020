<template lang="html">
  <div v-if="country">
    <h3>{{country.name}}</h3>
    <p>Population: {{country.population}}</p>
    <p>Region:{{country.region}}</p>
    <p v-for="(country, index) in countries">Languages Spoken: {{country.languages.name}}</p>
    <img class="med-flag" :src="country.flag"/>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
.med-flag {
  height: 40px
}
</style>
