<template>
  <div id="operation_box">
      <ul>
          <li v-for="(card_operator, index) in cards_and_operators" :card_operator="card_operator" :key="index">
               <img :src="card_operator.image">
               <!-- <span class="second-column"><button v-on:click="removeFromFavourites(beer)">Remove</button></span> -->
          </li>
      </ul>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: "operation_box",
    data() {
        return {
            cards_and_operators: []
        }
    },
    mounted(){
        eventBus.$on('add-to-operation-box', (card) => {
            // if(!this.favourites.includes(beer)){
            //     this.favourites.push(beer);
            // }else{
            //     alert(`${beer.name} has been added to favourites list already!`);
            // }
            this.cards_and_operators.push(card);       
        })
    }
}
</script>

<style lang="css" scoped>
#operation_box{
    border: 2px solid #1a681e;
}
ul{
    list-style-type: none;
}
li {
    float: left;
}
img{
    width: 100px;
}

</style>