<template>
    <div>
        <div class="detail-card">
            <div class="detail-card__img">
                <BackButton class="back-button"/>
            </div>
            <div class="detail-card__info">
                <div class="detail-card__scroll-tool">
                    <img src="../assets/images/scroll_tool.svg" alt="scroll">
                </div>
                <div class="detail-card__title">
                    Chicken Burger <br> Promo Pack
                </div>
                <div class="detail-card__rating">
                    <img src="../assets/images/star.svg" alt="star">
                    <span>
                        4,8 Rating
                    </span>
                </div>
                <div class="detail__card__descr">
                    Nulla occaecat velit laborum exercitation ullamco. Elit labore eu aute elit nostrud culpa velit excepteur deserunt sunt. Velit non est cillum consequat cupidatat ex Lorem laboris labore aliqua ad duis eu laborum.
                    <ul>
                        <li>Chicken</li>
                        <li>Tomatoa</li>
                        <li>Lettuse</li>
                    </ul>
                    Nulla occaecat velit laborum exercitation ullamco. Elit labore eu aute elit nostrud culpa velit excepteur deserunt sunt.
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import BackButton from './BackButton.vue';
    export default {
        name: 'DetailCard',
        components: {
            BackButton
        }
    }
</script>

<style scoped>
.detail-card__img {
    background-image: url('../assets/images/burger_1_detail.svg');
    height: 440px;
    background-position: center; 
    background-repeat: no-repeat; 
    background-size: cover; 
    padding-top: 38px;
    padding-left: 19px;
}
.detail-card__info {
    padding: 19.5px 34px 15px 34px;
    background: #FFFFFF;
    border-radius: 12px;
    margin-top: -70px;
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

.detail-card__rating {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 25px;
}

.detail-card__rating img {
    height: 19px;
    width: 19px;
}
.detail-card__rating span {
    font-weight: 400;
    font-size: 14px;
    line-height: 19px;
    color: #3B3B3B;
    opacity: 0.3;
}
</style>