<template>
    <div class="mainpage__wrapper">
        <UiInput/>
        <div class="mainpage__select-wrapper">
          <UiMultipleSelect class="mainpage__select"/>
        </div>
        <CardList/>
    </div>
</template>

<script>
import UiInput from './components/UI/UiInput.vue';
import UiMultipleSelect from './components/UI/UiMultipleSelect.vue';
import CardList from './components/CardList.vue';

export default {
  name: 'App',
  components: {
    UiInput,
    UiMultipleSelect,
    CardList,
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

#app {
  font-family: "Avenir", sans-serif;
  font-size: 12px;
  font-weight: 400;
  max-width: 375px;
  width: 100%;
  margin: 0 auto;
  padding: 24px 24px 0 24px;
  
}

* {
  box-sizing: border-box;
}

.mainpage__wrapper {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.mainpage__select-wrapper {
  position: relative; 
  height: 35px; 
}

.mainpage__select {
  position: absolute;
  z-index: 2;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>
