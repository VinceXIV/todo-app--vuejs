<template>
  <div class="container" :class="[theme, mode]">
    <img :src="imageDesktopDark" class="desktop dark" alt="Mountain">
    <img :src="imageDesktopLight" class="desktop light" alt="Mountain">
    <img :src="imageMobileDark" class="mobile dark" alt="Mountain">
    <img :src="imageMobileLight" class="mobile light" alt="Mountain">
    <div id="bottom-div" :class="theme"></div>
    <p :class="[theme, mode]">Drag and drop to reorder list</p>
  </div>
</template>

<script>
export default {
  name: 'BackGround',
  props: {
    theme: String,
    mode: String
  },

  data() {
    return {
      imageDesktopDark: require(`../assets/images/bg-desktop-dark.jpg`),
      imageDesktopLight: require(`../assets/images/bg-desktop-light.jpg`),
      imageMobileDark: require(`../assets/images/bg-mobile-dark.jpg`),
      imageMobileLight: require(`../assets/images/bg-mobile-light.jpg`)
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

  .dark .light, .light .dark, .desktop .mobile, .mobile .desktop {
    display: none;
  }

  .container p {
    position: absolute;
    width: calc(min(480px, 80vw));
    left: 0;
    right: 0;
    text-align: center;
    margin-left: auto;
    margin-right: auto;
  }

  .container p.mobile {
    bottom: 2rem;
  }

  .container p.desktop {
    bottom: 3.5rem;
  }

  .container p.dark {
    color: var(--dark-grayish-blue);
  }

  .container p.light {
    color: var(--light-grayish-blue);
  }
</style>
