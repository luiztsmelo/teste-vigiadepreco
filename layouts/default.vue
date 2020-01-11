<template>
  <div>
    <nuxt />
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'

export default {
  components: {
    Footer
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Roboto:400,500,700&display=swap');

html {
  font-family: 'Roboto', sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  color: #454344;
}
*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
</style>
