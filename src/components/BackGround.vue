<template>
  <div class="container">
    <img :src="image" alt="Mountain">
    <div id="bottom-div" :class="theme"></div>
  </div>
</template>

<script>
export default {
  name: 'BackGround',
  props: {
    theme: {
      type: String,
      default: 'dark'
    }
  },

  data() {
    return {
      image: require(`../assets/images/bg-desktop-${this.theme}.jpg`)
    }
  }
}
</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    height: 100vh;
    position: absolute;
    left: 0;
    top: 0;
  }

  img {
    width: 100vw;
    height: 33vh;
    margin: 0;
    padding: 0;
    object-fit: cover;
  }

  #bottom-div {
    height: 67vh;
  }

  #bottom-div.dark {
    background-color: var(--very-dark-blue)
  }

  #bottom-div.light {
    background-color: var(--very-light-gray)
  }
</style>
