<template>
	<div
		class="select"
		v-click-out-side="closeSelect"
	>
		<div
			class="select__placeholder"
			@click="clickSelect"
		>
			{{ getValue }}
		</div>
		<div
			class="select__option-list"
			:class="{ open: isOpen }"
		>
			<div
				v-for="(option, index) in options"
				:key="index"
				:value="option.value"
				class="select__option"
				:class="{ selected: this.selectedCategories.includes(option) }"
				@click="clickOption(option)"
			>
				{{ option.name }}
			</div>
		</div>
	</div>
</template>

<script>
import clickOutSide from '@mahdikhashan/vue3-click-outside';

export default {
	name: 'UiMultipleSelect',
	emits: ['update-categories'],
	directives: {
		clickOutSide,
	},
	data() {
		return {
			isOpen: false,
			defaultValue: 'Pick categories',
			selectedCategories: [],
			options: [
				{ name: 'Burger', value: 'burger' },
				{ name: 'Pizza', value: 'pizza' },
				{ name: 'Sandwich', value: 'sandwich' },
				{ name: 'Chicken', value: 'chicken' },
			],
		};
	},
	methods: {
		clickSelect() {
			this.isOpen = !this.isOpen;
		},
		closeSelect() {
			this.isOpen = false;
		},
		clickOption(option) {
			if (this.selectedCategories.includes(option)) {
				this.selectedCategories = this.selectedCategories.filter(
					(item) => item !== option
				);
			} else {
				this.selectedCategories.push(option);
			}

			this.$emit(
				'update-categories',
				this.selectedCategories.map((category) => category.value)
			);
		},
	},
	computed: {
		getValue() {
			if (this.selectedCategories.length) {
				return this.selectedCategories
					.reduce((acc, curr) => {
						acc.push(curr.name);
						return acc;
					}, [])
					.toString()
					.replaceAll(',', ', ');
			} else {
				return this.defaultValue;
			}
		},
	},
};
</script>

<style scoped>
.select {
	max-width: 176px;
	height: 36px;
	width: 100%;
}

.select__placeholder {
	border-radius: 7px;
	background: linear-gradient(98.81deg, #fff0f0 -0.82%, #ffdfdf 101.53%);
	margin-bottom: 2px;
	padding: 10px 12px;
	white-space: nowrap;
	overflow: hidden;
}

.select__option-list {
	display: none;
	border-radius: 7px;
	overflow: hidden;
	background: linear-gradient(98.81deg, #fff0f0 -0.82%, #ffdfdf 101.53%);
	mix-blend-mode: soft-light;
}

.select__option {
	padding: 10px 12px;
}

.select__option:hover {
	background: linear-gradient(98.81deg, #ffdada -0.82%, #ffdddd 101.53%);
}

.select__option.selected {
	background: linear-gradient(98.81deg, #fedada -0.82%, #ffcfcf 101.53%);
}

.select__option-list.open {
	display: block;
}
</style>
