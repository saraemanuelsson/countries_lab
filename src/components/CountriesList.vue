<template lang="html">
    <div>
        <ul>
            <list-item v-for="(country, index) in country" :country="country" :key="index"></list-item>
        </ul>
    </div>
  
</template>

<script>
import ListItem from "./ListItem.vue";

export default {

}
</script>

<style>

</style>