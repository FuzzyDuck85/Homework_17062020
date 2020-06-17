<template lang="html">
  <div class="selection" v-if="country">
    <h2>{{country.nativeName}}</h2>
    <h3>{{country.name}}</h3>
    <p>Population: {{country.population}}</p>
    <p>Capital City: {{country.capital}}</p>
    <p>Region:{{country.region}}</p>
    <p>Languages Spoken:</p>
    <ul>
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    <img class="siz-flag" :src="country.flag"/>
      <p v-for="currency in country.currencies">Currency: {{currency.name}} ({{currency.symbol}})</p>
    <p>Neighbouring Countries:</p>
    <ul>
      <li v-for="border in country.borders">{{border}}</li>
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
.siz-flag {
  height: 100px
}
</style>
