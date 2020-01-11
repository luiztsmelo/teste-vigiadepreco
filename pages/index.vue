<template>
  <section class="landing-page">
    <Navbar />

    <Header orientation="right" />

    <Features />

    <PromotionalVideo />

    <Stores />

    <Header orientation="left" />

    <Products :products="products" :stores="stores" />
  </section>
</template>

<script>
import Navbar from '../components/landing-page/Navbar.vue'
import Header from '../components/landing-page/Header.vue'
import Features from '../components/landing-page/Features.vue'
import PromotionalVideo from '../components/landing-page/PromotionalVideo.vue'
import Stores from '../components/landing-page/Stores.vue'
import Products from '../components/landing-page/Products.vue'

export default {
  components: {
    Navbar,
    Header,
    Features,
    PromotionalVideo,
    Stores,
    Products
  },
  head: {
    title: 'Vigia de preço'
  },
  data() {
    return {
      products: [],
      stores: []
    }
  },
  async asyncData({ $axios }) {
    try {
      const resProducts = await $axios.$get('https://api.myjson.com/bins/1gnnec')
      const resStores = await $axios.$get('https://api.myjson.com/bins/nher8')
      return {
        products: resProducts,
        stores: resStores
      }
    } catch (error) {
      console.error(error)
    }
  }
}
</script>

<style lang="scss">
.landing-page {
  overflow: hidden;
}
</style>
