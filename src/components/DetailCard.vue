<template>
	<div>
		<div class="detail-card">
			<div
				:style="{ 'background-image': `url(${card.image})` }"
				class="detail-card__img"
			>
				<BackButton
					class="back-button"
					@click="closeModal"
				/>
			</div>
			<div class="detail-card__info">
				<div class="detail-card__scroll-tool">
					<img
						src="../assets/images/scroll_tool.svg"
						alt="scroll"
					/>
				</div>
				<div class="detail-card__title">
					{{ card.title }}
				</div>
				<div class="detail-card__timer">
					<img
						src="../assets/images/timer.svg"
						alt="timer"
					/>
					<span> {{ card.readyInMinutes }} min </span>
				</div>
				<div
					v-html="card.summary"
					class="detail__card__descr"
				/>
			</div>
		</div>
	</div>
</template>

<script>
import BackButton from './BackButton.vue';
export default {
	name: 'DetailCard',
	props: ['card'],
	emits: ['close-modal'],
	components: {
		BackButton,
	},
	methods: {
		closeModal() {
			this.$emit('close-modal');
		},
	},
};
</script>

<style scoped>
.detail-card {
	background-color: rgba(237, 237, 237, 0.74);
}
.detail-card__img {
	height: 312px;
	background-position: center;
	background-repeat: no-repeat;
	background-size: contain;
	padding-top: 38px;
	padding-left: 19px;
}
.detail-card__info {
	padding: 19.5px 34px 15px 34px;
	background: #ffffff;
	border-top-left-radius: 14px;
	border-top-right-radius: 14px;
	margin-top: -50px;
	z-index: 4;
	position: relative;
}
.detail-card__scroll-tool {
	display: flex;
	justify-content: center;
	margin-bottom: 24.5px;
	cursor: pointer;
}
.detail-card__title {
	font-weight: 500;
	font-size: 27px;
	line-height: 35px;
	margin-bottom: 12px;
}

.detail-card__timer {
	display: flex;
	align-items: center;
	gap: 10px;
	margin-bottom: 25px;
}

.detail-card__timer img {
	width: 22px;
	height: 22px;
}
.detail-card__timer span {
	font-weight: 400;
	font-size: 14px;
	line-height: 19px;
	color: #3b3b3b;
	opacity: 0.3;
}
</style>
