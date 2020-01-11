<template>
  <LandingPageSection title="Marcas do app em destaque">
    <div class="stores-container">
      <div v-if="isMobile" class="stores-logos-grid-mobile">
        <div v-for="store in 9" :key="store" class="store-logo" :style="storeLogoStyles(store)">
          <img class="store-logo-img" src="../../assets/images/store-logo.png">
        </div>
      </div>

      <div class="stores-text-boxes">
        <div v-for="storeTextBox in storeTextBoxes" :key="storeTextBox.title" class="text-box">
          <h3 class="box-title">
            {{ storeTextBox.title }}
          </h3>
          <p class="box-text">
            {{ storeTextBox.text }}
          </p>
        </div>
      </div>

      <div v-if="!isMobile" class="stores-logos-grid-desktop">
        <div v-for="store in 16" :key="store" class="store-logo" :style="storeLogoStyles(store)">
          <img class="store-logo-img" src="../../assets/images/store-logo.png">
        </div>
      </div>
    </div>
  </LandingPageSection>
</template>

<script>
import mobile from 'is-mobile'
import LandingPageSection from './LandingPageSection.vue'

export default {
  components: {
    LandingPageSection
  },
  data() {
    return {
      isMobile: false,
      storeTextBoxes: [
        {
          title: 'Título 1',
          text: 'Marcação de texto para ser preenchido depois da página ficar pronta, enquanto isso segue com o texto marcando a página.'
        },
        {
          title: 'Título 2',
          text: 'Marcação de texto para ser preenchido depois da página ficar pronta, enquanto isso segue com o texto marcando a página.'
        },
        {
          title: 'Título 3',
          text: 'Marcação de texto para ser preenchido depois da página ficar pronta, enquanto isso segue com o texto marcando a página.'
        }
      ]
    }
  },
  mounted() {
    mobile() ? this.isMobile = true : this.isMobile = false
  },
  methods: {
    storeLogoStyles(store) {
      if (this.isMobile) {
        switch (store) {
          case 1: return { backgroundColor: '#1DA1F2' }
          case 5: return { backgroundColor: '#FF4600' }
          case 9: return { backgroundColor: '#9645D3' }
        }
      } else {
        switch (store) {
          case 1: return { backgroundColor: '#1DA1F2' }
          case 6: return { backgroundColor: '#FF4600' }
          case 11: return { backgroundColor: '#9645D3' }
          case 16: return { backgroundColor: '#F3D100' }
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>

.stores-container {
  display: grid;
  grid-template-columns: 1fr auto;
  grid-gap: 15%;
  align-items: center;
  width: 100%;
  .stores-text-boxes {
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 30px;
    .box-title {
      font-size: 21px;
      padding-bottom: 14px;
    }
    .box-text {
      font-size: 17px;
    }
  }
  .stores-logos-grid-desktop {
    display: grid;
    grid-template-columns: repeat(4, 80px);
    grid-template-rows: repeat(4, 80px);
    grid-gap: 18px;
    .store-logo {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      border-radius: 15px;
      box-shadow: 2px 2px 8px 1px rgba(0,0,0,.12);
      .store-logo-img {
        width: 50%;
        height: auto;
      }
    }
  }
  .stores-logos-grid-mobile {
    display: none;
  }
}

@media only screen and (max-width: 480px) {
  .stores-container {
    grid-template-columns: 1fr;
    grid-gap: 20px;
    .stores-text-boxes {
      display: grid;
      grid-template-columns: 1fr;
      grid-gap: 30px;
      margin-top: 20px;
      .box-title {
        text-align: center;
        font-size: 20px;
      }
      .box-text {
        text-align: center;
      }
    }
    .stores-logos-grid-mobile {
      display: grid;
      grid-template-columns: repeat(3, auto);
      grid-template-rows: repeat(3, auto);
      align-items: center;
      justify-items: center;
      grid-gap: 20px;
      .store-logo {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 70px;
        height: 70px;
        border-radius: 15px;
        box-shadow: 2px 2px 8px 1px rgba(0,0,0,.12);
        .store-logo-img {
          width: 50%;
          height: auto;
        }
      }
    }
    .stores-logos-grid-desktop {
      display: none;
    }
  }
}
</style>
