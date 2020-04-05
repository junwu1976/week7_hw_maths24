<template>
  <div id="operation_box">
      <ul>
          <li v-for="(card_operator, index) in cards_and_operators" :card_operator="card_operator" :key="index">
               <img :src="card_operator.image" v-on:click="remove(card_operator)">
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
    methods: {
      remove(card_operator) {
        eventBus.$emit('return-to-card-list',card_operator);
        const index = this.cards_and_operators.indexOf(card_operator);
        this.cards_and_operators.splice(index,1);
      }
    },
    mounted(){
        eventBus.$on('add-to-operation-box', (card) => {
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