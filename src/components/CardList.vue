<template>
    <div>
        <h1>Card List</h1>
        <ul>
            <card-item v-for="(card, index) in cards" :card="card" :key="index"></card-item>
        </ul>
    </div>
    
</template>

<script>
import { eventBus } from '../main.js';
import CardItem from './CardItem.vue';

export default {
    name: 'card-list',
    props: ['cards'],
    components: {
        "card-item": CardItem
    },
    mounted(){
        eventBus.$on('remove-from-card-list', (card) => {
            const index = this.cards.indexOf(card);
            this.cards.splice(index,1);
        })
    }
}
</script>

<style lang="css" scoped>
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
