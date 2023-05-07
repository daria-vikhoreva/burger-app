<template>
	<div class="wrapper">
		<div
			v-if="!isOpen"
			class="mainpage"
		>
			<UiInput v-model="searchValue" />

			<div class="mainpage__select-wrapper">
				<UiMultipleSelect class="mainpage__select" />
			</div>

			<CardList
				:cards="getFilteredCards"
				@click-card="openModal"
			/>
		</div>

		<div
			v-if="isOpen"
			class="detail-recipe"
		>
			<DetailCard
				:card="detailCard"
				@close-modal="closeModal"
			/>
		</div>

		<div
			v-if="loading"
			class="loader"
		>
			<UiLoader />
		</div>
	</div>
</template>

<script>
import axios from 'axios';

import UiInput from './components/UI/UiInput.vue';
import UiMultipleSelect from './components/UI/UiMultipleSelect.vue';
import CardList from './components/CardList.vue';
import DetailCard from './components/DetailCard.vue';
import UiLoader from './components/UI/UiLoader.vue';

export default {
	name: 'App',
	components: {
		UiInput,
		UiMultipleSelect,
		CardList,
		DetailCard,
		UiLoader,
	},
	data() {
		return {
			cards: [],
			loading: true,
			errored: false,
			isOpen: false,
			detailCard: {},
			searchValue: '',
		};
	},
	created() {
		axios
			.get(
				'https://api.spoonacular.com/recipes/complexSearch?apiKey=d635120e94d84e19a0b28560f4f85391&query=burger&addRecipeNutrition=true'
			)
			.then((response) => {
				this.cards = response.data.results;
			})
			.catch((error) => {
				console.log(error);
				this.errored = true;
			})
			.finally(() => (this.loading = false));
	},
	methods: {
		openModal(card) {
			this.isOpen = true;
			this.detailCard = card;
		},
		closeModal() {
			this.isOpen = false;
			this.detailCard = {};
		},
	},
	computed: {
		getFilteredCards() {
			return this.cards.filter((item) =>
				item.title
					.toLowerCase()
					.includes(this.searchValue.toLowerCase())
			);
		},
	},
};
</script>

<style>
@font-face {
	font-family: 'Avenir';
	src: local('Avenir'),
		url(./assets/fonts/AvenirLTStd-Black.otf) format('opentype');
	font-weight: 700;
}

@font-face {
	font-family: 'Avenir';
	src: local('Avenir'),
		url(./assets/fonts/AvenirLTStd-Book.otf) format('opentype');
	font-weight: 350;
}

@font-face {
	font-family: 'Avenir';
	src: local('Avenir'),
		url(./assets/fonts/AvenirLTStd-Roman.otf) format('opentype');
	font-weight: 400;
}

#app {
	font-family: 'Avenir', sans-serif;
	font-size: 12px;
	font-weight: 400;
	max-width: 375px;
	width: 100%;
	min-height: 785px;
	height: 100%;
	margin: 0 auto;
	padding: 24px 24px 0 24px;
}

* {
	box-sizing: border-box;
}

.wrapper {
	display: flex;
	flex-direction: column;
	gap: 40px;
}

.mainpage {
	display: flex;
	flex-direction: column;
	gap: 20px;
}

.mainpage__select-wrapper {
	position: relative;
	height: 35px;
}

.mainpage__select {
	position: absolute;
	z-index: 2;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
}

.loader {
	margin: 0 auto;
}
</style>
