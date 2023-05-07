<template>
	<div class="wrapper">
		<div
			v-if="!isOpen"
			class="mainpage"
		>
			<UiInput v-model="searchValue" />

			<div class="mainpage__select-wrapper">
				<UiMultipleSelect
					class="mainpage__select"
					@update-categories="changeSelectedCategories"
				/>
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
			loading: false,
			errored: false,
			isOpen: false,
			detailCard: {},
			searchValue: '',
			selectedQueries: [],
		};
	},
	created() {
		const localCards = localStorage.getItem('cards');

		if (localCards) {
			this.cards = JSON.parse(localCards);
			return;
		}

		this.loading = true;
		const queries = ['pizza', 'burger', 'sandwich', 'chicken'];

		const requests = queries.map((query) => {
			return axios.get(
				`https://api.spoonacular.com/recipes/complexSearch?apiKey=${process.env.VUE_APP_NOT_SECRET_CODE}&addRecipeNutrition=true&number=20&query=${query}`
			);
		});

		axios
			.all(requests)
			.then((responses) => {
				const data = [];

				for (const response of responses) {
					data.push(...response.data.results);
				}
				this.cards = data;
				localStorage.setItem('cards', JSON.stringify(data));
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
		changeSelectedCategories(selected) {
			this.selectedQueries = selected;
		},
	},
	computed: {
		getFilteredCards() {
			return this.cards.filter(
				(card) =>
					// 1 вариант: если title содержит строку поиска && title содержит одну из выбранных категорий
					// ||
					// 2 вариант: если title содержит строку поиска && категории не выбраны
					(card.title
						.toLowerCase()
						.includes(this.searchValue.toLowerCase()) &&
						this.selectedQueries.some((query) =>
							card.title.toLowerCase().includes(query)
						)) ||
					(card.title
						.toLowerCase()
						.includes(this.searchValue.toLowerCase()) &&
						!this.selectedQueries.length)
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
