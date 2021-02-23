<template>
  <div id="app">

    <label for="country_select">Select a Country:</label>
    <select id="country_select" v-model="selectedCountry" >
      <option disabled value="'">Select a country</option>
      <option v-for="country in countries" :key="country.alpha3code" :country="country" :value="country">{{country.name}}</option>
    </select>
    

    <country-detail v-if="selectedCountry" :countries="countries" :country="selectedCountry"></country-detail>

    <button v-on:click="addToFavourite">Add Country to favourites</button>

    <favourite-countries :favouriteCountries="favouriteCountries"></favourite-countries>
</div>

</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import FavouriteListItem from './components/FavouriteListItem.vue';

export default {
  name: 'App',
  data() {
    return {
      countries: [],
      countryNames: [],
      selectedCountry: null,
      favouriteCountries: []
    }
  },
  components: {
    'country-detail': CountryDetail,
    'favourite-countries': FavouriteListItem
  },
    mounted(){
      this.fetchCountry()
      
    },
    methods: {
      addToFavourite: function(){
      if (!this.favouriteCountries.includes(this.selectedCountry)){
        this.favouriteCountries.push(this.selectedCountry)
        }
      },
      fetchCountry: function(){
        const request = fetch("https://restcountries.eu/rest/v2/all")
          .then(result => result.json())
          .then(data => {
            for (let dat of data){
              this.countries.push(dat)
            }
          })
      }
  }
}
</script>

<style>
.small-flag {
  height: 20px
}



</style>
