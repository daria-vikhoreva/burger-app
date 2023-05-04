<template>
    <div class="card">
        <div class="card__rating rating">
            <img src="../assets/images/star.svg" alt="star" class="rating__img">
            3.8</div>
        <div class="card__img">
            <img src="../assets/images/burger_1.svg" alt="burger">
        </div>
        <div class="card__title">Chicken burger</div>
        <div class="card__descr">100 gr chicken + tomato + cheese  Lettuce</div>
        <div class="card__info">
            <div class="card__info-kcal">
                300 kcal
            </div>
            <button class="card__button">
                <img src="../assets/images/plus.svg" alt="plus">
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CardItem'
    }
</script>

<style scoped>
.card {
    max-width: 155px;
    height: 209px;
    padding: 8px 12px;
    box-shadow: 0px 1px 8px rgba(0, 0, 0, 0.12);
    border-radius: 10px;
    display: flex;
    flex-direction: column;
}

.card__rating {
    margin-bottom: 7px;
    display: flex;
    align-items: center;
    gap: 4px;
}

.card__img {
    margin: 0 auto;
    margin-bottom: 9px;
}

.card__title {
    font-size: 17px;
    font-weight: 300;
    margin-bottom: 8px;
}

.card__descr {
    word-spacing: -2px;
    margin-bottom: 6px;
}

.card__info {
    display: flex;
    gap: 49px;
    justify-content: center;
    align-items: center;
}

.card__info-kcal {
    font-size: 14px;
    font-weight: 700;
    color: #FF0000;
    letter-spacing: 0.3px;
    word-spacing: -1px;
}

.card__button {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    background-color: #FF0000;
    border: none;
    cursor: pointer;
    display: flex;
    padding: 6px;
}
</style>