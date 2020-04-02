<template lang='html'>
<div>
  <h1>BREW DOG IS FOR MANLY MEN</h1>
  <p>List of Beers: <beers-list :beers="beers" /></p>
  <p>List of Favourite Beers: <favourite-beers /></p>
  <beer-detail />
</div>
  
</template>

<script>
import { eventBus } from './main.js';
import BeerDetail from './components/BeerDetail.vue'
import BeersList from './components/BeersList.vue'
import FavouriteBeers from './components/FavouriteBeers.vue'


export default {
  name: 'brewdog',
  data() {
    return {
      beers: [],
      selectedBeer: null
    };
  },
  props: ['favouriteBeers'],
  mounted(){
    fetch('https://api.punkapi.com/v2/beers').then(response=> response.json())
    .then(beers=> this.beers= beers)
    .catch(error=> console.log(error))
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  }
}
</script>

<style scoped>

  div{
    background-color:deepskyblue;
  }


</style>