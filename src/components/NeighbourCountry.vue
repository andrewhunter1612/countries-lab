<template lang="html">
  <div id="neighbouring_countries">
  <h3>Neighbouring Countries</h3>
  
    <ul id="neighbouring_countries">
      <li  v-for="(border, index) in country.borders">
          neighbours.push(countries.filter((country) => {
            if (country.alpha3code === border)
              return country.name
          }))
          neighbours.data.border
          {{border}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    neighbours: []
  }
  name: 'neighbouring-countries',
  props: ['country', 'countries']
}
</script>

<style lang="css" scoped>

.med-flag {
  height: 40px
}
</style>
