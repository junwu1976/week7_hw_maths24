<template>
  <li>
      <span v-on:click="choose"><img :src="card.image"></span>
  </li>
</template>

<script>
export default {
    name: 'card-item',
    props: ['card'],
    methods: {
      choose() {
        eventBus.$emit('choose-card', this.card);
      }
    }
}
</script>

<style>
li {
    float: left;
}
img{
    width: 150px;
}
</style>