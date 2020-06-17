<template lang="html">
  <div class="">
    <select v-model="selectedCountry" v-on:change="handleChange">
      <option v-for="(country, index) in countries" :country="country" :key="index"></option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "list-item": ListItem
  },
  data(){
    return{
      selectedCountry: null
    }
  },
  methods: {
    handleChange(){
      eventBus$emit('country-select', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
