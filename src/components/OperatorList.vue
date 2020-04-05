<template>
  <div>
      <h1>Operator List</h1>
      <ul>
          <li v-on:click="choose" :value=selectedOperator>+</li>
          <li v-on:click="choose" :value=selectedOperator>-</li>
          <li v-on:click="choose" :value=selectedOperator>x</li>
          <li v-on:click="choose" :value=selectedOperator>&divide</li>
          <li v-on:click="choose" :value=selectedOperator>(</li>
          <li v-on:click="choose" :value=selectedOperator>)</li>
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
      choose() {
        alert(this.selectedOperator);
        // eventBus.$emit('add-to-operation-box', this.card);
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
