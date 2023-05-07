<template>
	<div class="back-button">
		<img
			src="../assets/images/path.svg"
			alt="back-path"
		/>
	</div>
</template>

<script>
export default {
	name: 'BackButton',
};
</script>

<style scoped>
.back-button {
	background: white;
	border-radius: 7px;
	padding: 14px 18px;
	max-width: max-content;
	display: flex;
	cursor: pointer;
}
</style>
