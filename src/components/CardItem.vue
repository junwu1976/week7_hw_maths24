<template>
  <li>
      <span v-on:click="choose"><img :src="card.image"></span>
  </li>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'card-item',
    props: ['card'],
    methods: {
      choose() {
        eventBus.$emit('add-to-operation-box', this.card);
        eventBus.$emit('remove-from-card-list', this.card);
      }
    }
}
</script>

<style lang="css" scoped>
li {
    float: left;
}
img{
    width: 150px;
}
</style>