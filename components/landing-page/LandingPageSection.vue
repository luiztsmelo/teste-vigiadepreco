<template>
  <section class="landing-page-section" :style="landingPageSectionStyles">
    <h2 v-if="title !== ''" class="title" :style="titleStyles">
      {{ title }}
    </h2>
    <p v-if="subtitle !== ''" class="subtitle">
      {{ subtitle }}
    </p>
    <slot />
  </section>
</template>

<script>
export default {
  props: {
    title: { type: String, default: '', required: false },
    subtitle: { type: String, default: '', required: false },
    bgColor: { type: String, default: '#fff', required: false }
  },
  computed: {
    landingPageSectionStyles() {
      return {
        backgroundColor: this.bgColor
      }
    },
    titleStyles() {
      return {
        marginBottom: this.subtitle === '' ? '40px' : '15px'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.landing-page-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 5rem 10%;
  .title {
    text-align: center;
    font-size: 37px;
    font-weight: 700;
    padding: 0 15%;
  }
  .subtitle {
    text-align: center;
    padding: 0 15%;
    margin-bottom: 30px;
  }
}

@media only screen and (max-width: 480px) {
  .landing-page-section {
    padding: 3.5rem 7%;
    .title {
      font-size: 30px;
      padding: 0;
    }
    .subtitle {
      padding: 0;
      margin-bottom: 30px;
    }
  }
}
</style>
