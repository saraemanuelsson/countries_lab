<template lang="html">
    <div>
        <form v-on:submit.prevent="handleClick">
            <label for="country">Country:</label>
            <select name="country" id="country"  v-model="selectedCountry">
                <option v-for="(country, index) in countries" :value="country">{{country.name}}</option>
            </select>
            <input type="submit" value="Select">
        </form>
    </div>
  
</template>

<script>
import ListItem from "./ListItem.vue";
import { eventBus } from '../main.js';

export default {
    name: "countries-list",
    props: ["countries", "selectedCountry"],
    components: {
        "list-item": ListItem
    },
    methods: {
            handleClick(){
            eventBus.$emit('country-selected', this.selectedCountry)
        }
    }
}
</script>

<style>
 ul {
     list-style: none;
 }
</style>