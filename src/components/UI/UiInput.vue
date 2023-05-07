<template>
	<div>
		<input
			type="text"
			class="input"
			placeholder="Search"
			:value="modelValue"
			@input="$emit('update:modelValue', $event.target.value)"
		/>
	</div>
</template>

<script>
export default {
	name: 'UiInput',
	props: ['modelValue'],
	emits: ['update:modelValue'],
};
</script>

<style scoped>
.input {
	background: linear-gradient(98.81deg, #fff0f0 -0.82%, #ffdfdf 101.53%);
	border-radius: 7px;
	padding: 10px 18px;
	width: 100%;
	border: none;
}
.input::placeholder {
	font-size: 12px;
	color: #000;
	opacity: 0.9;
}
</style>
