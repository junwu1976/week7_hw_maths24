<template>
    <div>
        <h1>Card List</h1>
        <ul>
            <card-item v-for="(card, index) in cards" :card="card" :key="index"></card-item>
        </ul>
    </div>
    
</template>

<script>
import CardItem from './CardItem.vue';

export default {
    name: 'card-list',
    props: ['cards'],
    components: {
        "card-item": CardItem
    }
}
</script>

<style lang="css" scoped>
ul{
    list-style-type: none;
}
</style>
