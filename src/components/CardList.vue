<template>
    <div class="card-list">
        <div
        v-for="card in cards"
        :key="card.id">
            <CardItem :card="card"/>
        </div>
    </div>
</template>

<script>
import CardItem from './CardItem.vue';

    export default {
        name: 'CardList',
        props: ['cards'],
        components: {
            CardItem
        }
    }
</script>

<style scoped>
.card-list {
    display: flex;
    gap: 17px;
    flex-wrap: wrap;
}
</style>