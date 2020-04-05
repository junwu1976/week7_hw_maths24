<template>
  <div id="app">
    <h1>Game description</h1>
    <p>The 24 Game is an arithmetical card game in which the objective is to find a way to manipulate four integers 
      so that the end result is 24. For example, for the card with the numbers 4, 7, 8, 8, a possible solution is 
      (7 - (8 &divide 8)) x 4 = 24.

The game has been played in Shanghai since the 1960s, using playing cards. It has been known by other names, 
including Maths24, but these products are not associated with the copyrighted versions of the 24® Game.</p> 
    <h1>Rules</h1>
    <p>No jokers. A=1,2=2...10=10,JACK=11,QUEEN=12,KING=13</p>
    <card-list :cards="cards"></card-list>
    <operator-list></operator-list>
    <operation-box></operation-box>
  </div>
</template>

<script>
import CardList from './components/CardList.vue';
import OperatorList from './components/OperatorList.vue';
import OperationBox from './components/OperationBox.vue';

export default {
  name: 'App',
  data() {
    return {
      cards: []
 //     selectedCard: null
    }
  },
  components: {
    "card-list": CardList,
    "operator-list": OperatorList,
    "operation-box": OperationBox
  },
  mounted(){
    fetch('https://deckofcardsapi.com/api/deck/new/draw/?count=4')
    .then(response => response.json())
    .then(cardsInfo => this.cards = cardsInfo.cards)

    // eventBus.$on('beer-selected', (beer) => {
    //   this.selectedBeer = beer
    // })
  }
}


</script>

<style lang="css" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}
</style>
