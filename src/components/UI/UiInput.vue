<template>
    <div>
        <input type="text" class="input" placeholder="Search">
    </div>
</template>

<script>
    export default {
        name: 'UiInput'
    }
</script>

<style scoped>
.input {
    background: linear-gradient(98.81deg, #FFF0F0 -0.82%, #FFDFDF 101.53%);
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