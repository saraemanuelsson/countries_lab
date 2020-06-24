<template lang="html">
  <div v-if="country">
      <h2>{{country.name}}</h2>
      <p>Capital: {{country.capital}}</p>
      <p>Population: {{country.population}}</p>
      <p>Languages Spoken: {{country.languages.name}}</p>
      <p v-for="language in country.languages">{{language.name}}</p>
      <img :src="country.flag" alt="Flag" id="flag">
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'country-detail',
    props: ['country']

}
</script>

<style>

#flag {
    width: 400px;
    height: auto;
}

</style>