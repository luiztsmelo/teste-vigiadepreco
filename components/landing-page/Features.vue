<template>
  <LandingPageSection bg-color="#f7ffdc">
    <div class="features-grid">
      <img class="shape-2" src="../../assets/images/shape-2.svg">

      <div v-for="feature in features" :key="feature.title" class="feature">
        <img class="feature-img" :src="featureImgSrc(feature)" :srcset="`../../assets/images/${feature.img}@2x.png 2x, ../../assets/images/${feature.img}@3x.png 3x`">

        <h3 class="feature-title">
          {{ feature.title }}
        </h3>

        <p class="feature-text">
          {{ feature.text }}
        </p>
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
  data() {
    return {
      features: [
        {
          img: 'group-33',
          title: 'Título 1',
          text: 'Texto corrido com informações que vão ser preenchidas depois que a página estiver pronta.'
        },
        {
          img: 'alarm-clock-2',
          title: 'Título 2',
          text: 'Texto corrido com informações que vão ser preenchidas depois que a página estiver pronta.'
        },
        {
          img: 'ic-notifications-none',
          title: 'Título 3',
          text: 'Texto corrido com informações que vão ser preenchidas depois que a página estiver pronta.'
        }
      ]
    }
  },
  methods: {
    featureImgSrc(feature) {
      // It's not possible to dynamically change img src inline. We need to require it.
      return require(`../../assets/images/${feature.img}.png`)
    }
  }
}
</script>

<style lang="scss" scoped>
.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 30px;
  position: relative;
  .shape-2 {
    position: absolute;
    top: -200px;
    left: -250px;
    width: 350px;
    z-index: 1;
  }
  .feature {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: #fff;
    padding: 55px 35px;
    border-radius: 15px;
    box-shadow: 3px 3px 12px 1px rgba(0,0,0,.12);
    z-index: 2;
    .feature-img {
      width: 45px;
    }
    .feature-title {
      font-size: 21px;
      padding: 27px 0 14px;
      text-align: center;
    }
    .feature-text {
      font-size: 17px;
      text-align: center;
    }
  }
}

@media only screen and (max-width: 480px) {
  .features-grid {
    grid-template-columns: 1fr;
    .shape-2 {
      top: -150px;
      left: -250px;
      width: 300px;
    }
    .feature {
      padding: 45px 25px;
      .feature-img {
      }
      .feature-title {
        font-size: 20px;
      }
      .feature-text {
      }
    }
  }
}
</style>
