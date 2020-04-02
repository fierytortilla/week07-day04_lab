<template lang='html'>
<div>
    <select id="favouriteBeersList" v-bind="favouriteBeers" v-model="selectedBeer" v-on:change="handleSelect">Select a favourited beer
        <option disabled value="">Select a favourited beer</option>
        <option v-for="beer in favouriteBeers" :value="beer">{{beer.name}}</option>
    </select>

</div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
    name: 'favourite-beers',
    data(){
        return{
            favouriteBeers:[],
            selectedBeer: {}
        }
    },
    mounted(){
        eventBus.$on('beer-favourited', (beer)=>{
            if(!this.favouriteBeers.includes(beer)){
                this.favouriteBeers.push(beer)
            }
        })
    },
    methods:{
        handleSelect(){
            eventBus.$emit('beer-selected', this.selectedBeer)
        }
    }

}
</script>

<style scoped>

</style>