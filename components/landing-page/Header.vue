<template>
  <LandingPageSection>
    <div class="header-container">
      <img v-if="orientation === 'right'" class="shape-1" src="../../assets/images/shape-1.svg">
      <img v-if="orientation === 'left'" class="shape-3" src="../../assets/images/shape-3.svg">

      <div v-if="orientation === 'left'" class="phone-img-wrapper">
        <img class="phone-img" src="../../assets/images/group-11.png" alt="Imagem do app">
      </div>

      <div class="headline-wrapper">
        <h1 class="headline">
          Título da página
        </h1>
        <p class="subheadline">
          Informação curta e direta sobre o app divulgado na página com foco nas funcionalidades.
        </p>
        <div class="app-download-links">
          <a class="link" href="https://play.google.com/" target="__blank">
            <img class="link-img" src="../../assets/images/google-play.png" alt="Download na Google Play">
          </a>
          <a class="link" href="https://www.apple.com/ios/app-store/" target="__blank">
            <img class="link-img" src="../../assets/images/app-store.png" alt="Download na App Store">
          </a>
        </div>
      </div>

      <div v-if="orientation === 'right'" class="phone-img-wrapper">
        <img class="phone-img" src="../../assets/images/group-9.png" alt="Imagem do app">
      </div>
    </div>
  </LandingPageSection>
</template>

<script>
import LandingPageSection from './LandingPageSection.vue'

export default {
  components: {
    LandingPageSection
  },
  props: {
    orientation: { type: String, default: 'right', required: true }
  }
}
</script>

<style lang="scss" scoped>
.header-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  justify-content: center;
  grid-gap: 30px;
  position: relative;
  .shape-1 {
    position: absolute;
    right: -600px;
    top: -1020px;
    width: 1300px;
  }
  .shape-3 {
    position: absolute;
    left: -400px;
    top: -300px;
    width: 1000px;
  }
  .headline-wrapper {
    .headline {
      font-size: 41px;
      font-weight: 700;
      margin-bottom: 12px;
    }
    .subheadline {
      font-size: 19px;
      font-weight: 400;
    }
    .app-download-links {
      display: flex;
      align-items: center;
      margin-top: 50px;
      .link {
        margin-right: 12px;
        .link-img {
          height: 50px;
        }
      }
    }
  }
  .phone-img-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    .phone-img {
      width: 350px;
      z-index: 2;
    }
  }
}

@media only screen and (max-width: 480px) {
  .header-container {
    grid-template-columns: 1fr;
    .shape-1 {
      display: none;
    }
    .shape-3 {
      display: none;
    }
    .headline-wrapper {
      display: flex;
      flex-direction: column;
      align-items: center;
      .headline {
        text-align: center;
        font-size: 32px;
      }
      .subheadline {
        text-align: center;
        font-size: 18px;
      }
      .app-download-links {
        margin-top: 30px;
        .link {
          .link-img {
            height: 40px;
          }
        }
      }
    }
    .phone-img-wrapper {
      .phone-img {
        width: 60%;
      }
    }
  }
}
</style>
