<template>
  <div>
    <h1>Around the World in 250 Clicks!</h1><br>
    <div class="drop-down">
      <country-select :countries="countries"></country-select>
    </div>
    <div class="main-container">
      <country-detail :country="selectedCountry"></country-detail>
    </div>
  </div>

</template>

<script>
import {eventBus} from './main.js';
import CountrySelector from './components/CountrySelector.vue';
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
export default {
  name: 'app',
  data(){
    return {
      countries:[],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries => this.countries = countries)
    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "country-select": CountrySelector,
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style>
.drop-down {
  display: flex;
  justify-content: space-around;
}
.main-container {
  display: flex;
  justify-content: space-around;
}
body{
  background: lightgreen;
}
h1{
  color: black;
	font-family: tahoma;
	text-align: center;
  margin: 0.5rem 0.5rem;
  padding: 0.5rem 0.8rem;
  border: 5px solid #20437c;
  border-radius: 2%;
  border-style: double;
  background: #ddeaff;
}
.selection{
	color: black;
	font-family: tahoma;
	text-align: center;
  margin: 0.5rem 0.5rem;
  padding: 0.5rem 0.8rem;
  border: 5px solid #20437c;
  border-radius: 2%;
  border-style: double;
  background: #ddeaff;
  position: relative;
  font-family: Arial;
}
</style>
