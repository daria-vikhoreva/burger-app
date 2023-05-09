<template>
	<div
		class="card"
		@click="clickCard"
	>
		<div class="card__timer timer">
			<img
				src="../assets/images/timer.svg"
				alt="timer"
				class="timer__img"
			/>
			{{ card.readyInMinutes }} min
		</div>

		<div class="card__img">
			<img
				:src="card.image"
				alt="burger"
			/>
		</div>

		<div
			:title="card.title"
			class="card__title"
		>
			{{ card.title }}
		</div>

		<div
			:title="getDishTypes"
			class="card__descr"
		>
			{{ getDishTypes }}
		</div>

		<div class="card__kcal">
			{{ getKcal }}
		</div>
	</div>
</template>

<script>
export default {
	name: 'CardItem',
	props: ['card'],
	emits: ['click-card'],
	methods: {
		clickCard() {
			this.$emit('click-card', this.card);
		},
	},
	computed: {
		getKcal() {
			return (
				Math.round(this.card.nutrition.nutrients[0].amount) + ' kcal'
			);
		},
		getDishTypes() {
			return this.card.dishTypes.join(', ');
		},
	},
};
</script>

<style scoped>
.card {
	max-width: 155px;
	max-height: 312px;
	height: 100%;
	padding: 10px 12px;
	box-shadow: 0px 1px 8px rgba(0, 0, 0, 0.12);
	border-radius: 10px;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}

.card__timer {
	margin-bottom: 7px;
	display: flex;
	align-items: center;
	gap: 4px;
}

.timer__img {
	width: 22px;
	height: 22px;
}

.card__img {
	margin: 0 auto;
	margin-bottom: 9px;
	height: 150px;
	display: flex;
}

.card__img img {
	max-width: 100%;
	max-height: 100%;
	object-fit: contain;
}
.card__title {
	font-size: 17px;
	font-weight: 300;
	margin-bottom: 10px;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}

.card__descr {
	word-spacing: -2px;
	margin-bottom: 6px;
	opacity: 0.5;
	height: 30.4px;
	overflow: hidden;
}

.card__kcal {
	font-size: 14px;
	font-weight: 700;
	color: #ff0000;
	letter-spacing: 0.3px;
	word-spacing: -1px;
}
</style>
