<template>
    <div class="wrapper">
        <CardItem/>
        <UiButton/>
        <UiInput/>
        <UiMultipleSelect/>
        <UiCheckbox/>
    </div>
</template>

<script>
import CardItem from './components/CardItem.vue';
import UiButton from './components/UI/UiButton.vue';
import UiInput from './components/UI/UiInput.vue';
import UiCheckbox from './components/UI/UiCheckbox.vue';
import UiMultipleSelect from './components/UI/UiMultipleSelect.vue';

export default {
  name: 'App',
  components: {
    CardItem,
    UiButton,
    UiInput,
    UiCheckbox,
    UiMultipleSelect,
  }
}
</script>

<style>

@font-face {
  font-family: "Avenir";
  src: local("Avenir"),  
  url(./assets/fonts/AvenirLTStd-Black.otf) format("opentype");
  font-weight: 700;
}

@font-face {
  font-family: "Avenir";
  src: local("Avenir"),  
  url(./assets/fonts/AvenirLTStd-Book.otf) format("opentype");
  font-weight: 350;
}

@font-face {
  font-family: "Avenir";
  src: local("Avenir"),  
  url(./assets/fonts/AvenirLTStd-Roman.otf) format("opentype");
  font-weight: 400;
}

.wrapper {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

#app {
  font-family: "Avenir", sans-serif;
  margin-top: 60px;
  font-size: 12px;
  font-weight: 400;
  margin-left: 60px;
}

* {
  box-sizing: border-box;
}
</style>
