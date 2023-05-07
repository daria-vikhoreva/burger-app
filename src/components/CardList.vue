<template>
	<div class="card-list">
		<div
			v-for="card in cards"
			:key="card.id"
		>
			<CardItem
				:card="card"
				@click-card="clickCard"
			/>
		</div>
	</div>
</template>

<script>
import CardItem from './CardItem.vue';

export default {
	name: 'CardList',
	props: ['cards'],
	emits: ['click-card'],
	components: {
		CardItem,
	},
	methods: {
		clickCard(card) {
			this.$emit('click-card', card);
		},
	},
};
</script>

<style scoped>
.card-list {
	display: flex;
	gap: 17px;
	flex-wrap: wrap;
}
</style>
