<template>
	<div>
		<img
			src="../../assets/images/loader.svg"
			class="loader"
			alt="loader"
		/>
	</div>
</template>

<script>
export default {
	name: 'UiLoader',
};
</script>

<style scoped>
@keyframes loading {
	from {
		transform: rotate(0deg);
	}
	to {
		transform: rotate(360deg);
	}
}

.loader {
	animation: 1s linear infinite loading;
}
</style>
