<template>
    <div>
        <input type="checkbox" id="checkbox" class="checkbox">
        <label for="checkbox"></label>
    </div>
</template>

<script>
    export default {
        name: 'UiCheckbox'
    }
</script>

<style scoped>
.checkbox {
    position: absolute;
    z-index: -1;
    opacity: 0;
}

.checkbox+label {
    display: inline-flex;
    align-items: center;
    user-select: none;
}

.checkbox+label::before {
    content: '';
    display: inline-block;
    width: 20px;
    height: 20px; 
    border-radius: 7px;
    background: linear-gradient(98.81deg, #FFF0F0 -0.82%, #FFDFDF 101.53%);
    background-repeat: no-repeat;
    background-position: center center;
    background-size: 100%;
}

.checkbox:checked+label::before {
    content: url(../../assets/images/check.svg);
    display: flex;
    justify-content: center;
    align-items: center;
}

.checkbox:disabled+label::before {
    content: url(../../assets/images/check.svg);
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.5;
}
</style>