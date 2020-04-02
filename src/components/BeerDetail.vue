<template>
<div v-if="beer" id="beerDetail">
    <h3><span>Name: </span>{{beer.name}}</h3>
    <button v-on:click='handleClick'>Favourite this beer!</button>
    <p><span>Alcohol: </span>{{beer.abv}}%</p>
    <p>Ingredients: </p>
    <!-- <ul>
        <li v-for="ingredients in beer['ingredients']"></li>
    </ul> -->
    <img :src="beer.image_url" alt="">
</div>
  
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: "beer-detail",
    data(){
        return {
            beer: null
        }
    },
    mounted(){
        eventBus.$on('beer-selected', (beer)=>{this.beer= beer})
    },
    methods: {
        handleClick(){
            eventBus.$emit('beer-favourited', this.beer)
        }
    } 


}
</script>

<style scoped>

img{
    width: 20%;
}

</style>