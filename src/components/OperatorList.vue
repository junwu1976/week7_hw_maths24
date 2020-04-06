<template>
  <div>
      <h1>Operator List</h1>
      <ul>
          <li v-on:click="choose(0,$event)" :value=selectedOperator>+</li>
          <li v-on:click="choose(1,$event)" :value=selectedOperator>-</li>
          <li v-on:click="choose(2,$event)" :value=selectedOperator>*</li>
          <li v-on:click="choose(3,$event)" :value=selectedOperator>/</li>
          <li v-on:click="choose(4,$event)" :value=selectedOperator>(</li>
          <li v-on:click="choose(5,$event)" :value=selectedOperator>)</li>
      </ul>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'operator-list',
    data() {
        return {
            selectedOperator: null
        }
    },
    methods: {
      choose(index,event) {
        this.selectedOperatorIndex = index;
        const li_value = event.currentTarget.innerText;
        this.selectedOperator = {"value":li_value,"image":"no"};
        // alert(this.selectedOperator);
        eventBus.$emit('add-operator-to-operation-box', this.selectedOperator);
      }
    }
}
</script>

<style lang="css" scoped>
ul{
    list-style-type: none;
}
li{
    padding: 10px;
    font-size: 100px;
    float: left;
}
li:hover {
    background-color: #bbb;
}
</style>
