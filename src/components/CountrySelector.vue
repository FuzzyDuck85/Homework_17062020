<template lang="html">
  <div>
    <select v-model="selectedCountry" v-on:change="handleChange" >
      <option v-for="(country, index) in countries" :value="country" :key="index" >{{ country.name }}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
  name: 'country-select',
  props: ['countries'],
  data(){
    return {
      selectedChange: null
    }
  },
  methods: {
    handleChange(){
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
