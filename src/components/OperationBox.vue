<template>
  <div id="operation_box">
      <ul>
          <li v-for="(card_operator, index) in cards_and_operators" :card_operator="card_operator" :key="index">
              <div v-if="hasImage(card_operator)">
                   <img :src="card_operator.image" v-on:click="remove(card_operator)">
              </div>
              <div v-else v-on:click="removeOperator(card_operator)">
                  {{ card_operator.value }}
              </div>
          </li>
      </ul>
       <div class="result_match" v-if="remainingCards > 0">Please use all cards</div>
       <div class="result_match" v-if="match24">Yes,you did it!{{ result }}</div>
       <div class="result_not_match" v-else>Sorry {{ result }}Did not match 24!! </div>
      <button v-on:click="calculate()">Calculate!</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: "operation_box",
    props: ['remainingCards'],
    data() {
        return {
            cards_and_operators: [],
            result: 0
        }
    },
    methods: {
      remove(card_operator) {
        eventBus.$emit('return-to-card-list',card_operator);
        const index = this.cards_and_operators.indexOf(card_operator);
        this.cards_and_operators.splice(index,1);
      },
      removeOperator(card_operator){
          const index = this.cards_and_operators.indexOf(card_operator);
          this.cards_and_operators.splice(index,1);
      },
      hasImage(card_operator){
            return "no" === card_operator.image ? false:true;
      },
      transform(){
          this.cards_and_operators.forEach(card_operator => {
              if(card_operator.value === "ACE"){
                  card_operator.value = 1;
              }else if(card_operator.value === "JACK"){
                  card_operator.value = 11;
              }else if(card_operator.value === "QUEEN"){
                  card_operator.value = 12;
              }else if(card_operator.value === "KING"){
                  card_operator.value = 13;
              }
          })
      },
      calculate(){
          this.transform();
          const express_result = this.cards_and_operators.reduce(function (express,card_operator){
              return express + card_operator.value
          },"");
          this.result = eval(express_result);
      }
    },
    computed: {
        match24(){
            return 24 === this.result ? true:false;
        }
    },
    mounted(){
        eventBus.$on('add-to-operation-box', (card) => {
            this.cards_and_operators.push(card);       
        })
        eventBus.$on('add-operator-to-operation-box',(operator)=>{
            this.cards_and_operators.push(operator);
        })
    }
}
</script>

<style lang="css" scoped>
#operation_box{
    border: 2px solid #1a681e;
}
.result_match{
    float: right;
    font-size: 30px;
    color: green;
}
.result_not_match{
    float: right;
    font-size: 30px;
    color: red;
}

ul{
    list-style-type: none;
}
li {
    float: left;
    font-size: 100px;
}
img{
    width: 100px;
}
button{
    padding: 20px;
    float: right;
    width: 125px;
    height: 50px;
    background-color: red;
    font-size: 20px;
}

</style>