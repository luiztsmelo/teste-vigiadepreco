<template>
  <LandingPageSection title="Vídeo promocional do app" subtitle="O vídeo mostra todas as funcionalidades e você vai conferir como funciona e ver como é fácil e simples de usar o app, falando do uso e seus benefícios.">
    <div class="promotional-video-container">
      <div class="video-wrapper">
        <iframe src="https://www.youtube.com/embed/kI2s7Tly2Pw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" class="video" />
      </div>
    </div>
  </LandingPageSection>
</template>

<script>
import LandingPageSection from './LandingPageSection.vue'

export default {
  components: {
    LandingPageSection
  }
}
</script>

<style lang="scss" scoped>
.promotional-video-container {
  padding: 0 15%;
  width: 100%;
  .video-wrapper {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 56.25%;
    border-radius: 15px;
    overflow: hidden;
    .video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }
  }
}

@media only screen and (max-width: 480px) {
  .promotional-video-container {
    padding: 0;
    .video-wrapper {
      .video {
      }
    }
  }
}
</style>
