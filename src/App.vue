<template>
  <BackGround theme='light'/>
  <ToDo theme='light'/>
</template>

<script>
import BackGround from './components/BackGround.vue'
import ToDo from './components/ToDo.vue';

export default {
  name: 'App',
  components: {
    BackGround,
    ToDo
  }
}
</script>

<style>
:root {
  /* COLORS */
  /* light theme */
  --very-light-gray: hsl(0, 0%, 98%);
  --very-light-grayish-blue: hsl(236, 33%, 92%);
  --light-grayish-blue: hsl(233, 11%, 84%);
  --dark-grayish-blue: hsl(236, 9%, 61%);
  --very-dark-grayish-blue: hsl(235, 19%, 35%);

  /* dark theme  */
  --very-dark-blue: hsl(235, 21%, 11%);
  --very-dark-desaturated-blue: hsl(235, 24%, 19%);
  --light-grayish-blue: hsl(234, 39%, 85%);
  --light-grayish-blue-hover: hsl(236, 33%, 92%);
  --dark-grayish-blue: hsl(234, 11%, 52%);
  --very-dark-grayish-blue: hsl(233, 14%, 35%);
  --very-dark-grayish-blue-2: hsl(237, 14%, 26%);

  /* TYPOGRAPHY  */
  --primary-font-size: 19px;
  --primary-font-family: 'Rubik', sans-serif;
  --font-weight-light: 400;
  --font-weight-bold: 700;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
