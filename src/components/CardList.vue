<template>
    <div>
        <div class="card-list">
            <CardItem/>
            <CardItem/>
            <CardItem/>
            <CardItem/>
            <CardItem/>
            <CardItem/>
        </div>
    </div>
</template>

<script>
import CardItem from './CardItem.vue';

    export default {
        name: 'CardList',
        components: {
            CardItem,
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