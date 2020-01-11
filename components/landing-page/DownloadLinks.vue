<template>
  <div class="download-links-container">
    <div class="chrome-extension-wrapper">
      <img class="chrome-img" src="../../assets/images/chrome.png" alt="Chrome">
      <p class="text">
        <b>Instale a extensão no seu Google Chrome.</b>
        <span>Texto de suporte do título</span>
      </p>
    </div>

    <div class="app-stores-wrapper">
      <p class="text">
        <b>Baixe nosso app</b>
        <span>e não fique de fora do que acontece no produto.</span>
      </p>
      <img class="app-store-img" src="../../assets/images/google-play.png" alt="Download na Google Play">
      <img class="app-store-img" src="../../assets/images/app-store.png" alt="Download na App Store">
    </div>
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
.download-links-container {
  display: grid;
  grid-template-columns: auto auto;
  align-items: center;
  grid-gap: 120px;
  .text {
    color: #000;
  }
  .chrome-extension-wrapper {
    display: grid;
    grid-template-columns: auto 1fr;
    align-items: center;
    grid-gap: 15px;
    .chrome-img {
    }
  }
  .app-stores-wrapper {
    display: grid;
    grid-template-columns: 1fr auto auto;
    align-items: center;
    grid-gap: 15px;
    .app-store-img {
      height: 42px;
    }
  }
}
</style>
