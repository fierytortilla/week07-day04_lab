<template lang='html'>
<div>
    <select id="beer-selector" v-model="selectedBeer" v-on:change="handleClick">
        <option disabled value="">Select a beer</option>
        <option v-for="beer in beers" :value="beer">{{beer.name}}</option>
    </select>

</div>
  
</template>

<script>
import { eventBus } from '../main.js';


export default {
    name: "beers-list",
    data(){
        return{
            'selectedBeer': {}
        }
    },
    props: ["beers"],
    methods:{
    handleClick(){
        eventBus.$emit('beer-selected', this.selectedBeer)
        }
    }

}
</script>

<style scoped>

</style>