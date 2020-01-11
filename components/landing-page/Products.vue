<template>
  <LandingPageSection title="Produtos mais acessados">
    <div class="products-swiper-container">
      <img
        class="arrow arrow-previous"
        src="../../assets/images/seta.png"
        :style="arrowDisabledStyle('left')"
        @click="swipeProducts('previous')"
      >

      <div ref="productsSwiper" class="products-swiper">
        <div v-for="product in products" :key="product.id" ref="product" class="product">
          <div class="price-variation-tag" :style="priceVariationTagStyle(product)">
            <img class="price-variation-arrow" src="../../assets/images/price-variation-arrow.svg" :style="priceVariationArrowStyle(product)">
            <p class="price-variation-value">
              {{ priceVariationValue(product) }}
            </p>
          </div>

          <a href="#" class="product-image-link">
            <img :src="product.image" class="product-image" loading="lazy" height="95">
          </a>

          <a href="#" class="product-title">
            {{ truncateTitle(product) }}
          </a>

          <p class="product-store">
            Vendido por <a href="#" class="product-store-link">{{ storeName(product) }}</a>
          </p>

          <a class="product-price" href="#">
            {{ product.price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' }) }}
          </a>
        </div>
      </div>

      <img
        class="arrow arrow-next"
        src="../../assets/images/seta.png"
        :style="arrowDisabledStyle('right')"
        @click="swipeProducts('next')"
      >
    </div>

    <a href="#">
      <button class="see-more-button">
        Ver mais
      </button>
    </a>
  </LandingPageSection>
</template>

<script>
import mobile from 'is-mobile'
import LandingPageSection from './LandingPageSection.vue'

export default {
  components: {
    LandingPageSection
  },
  props: {
    products: { type: Array, default() { return [] } },
    stores: { type: Array, default() { return [] } }
  },
  data() {
    return {
      productsSwiperWidth: 0,
      cardsNumber: 4,
      distanceFromStart: 0,
      maxDistancePossible: 0
    }
  },
  mounted() {
    if (mobile()) this.cardsNumber = 1.1
    this.productsSwiperWidth = this.$refs.productsSwiper.clientWidth
    this.maxDistancePossible = (this.productsSwiperWidth * this.products.length / this.cardsNumber) - this.productsSwiperWidth
    for (const product of Array.from(this.$refs.productsSwiper.children)) {
      const productSideMargins = 20
      const productWidth = `${(this.productsSwiperWidth / this.cardsNumber) - productSideMargins}px`
      // It's not possible to set width in this case, so we need to set both minWidth and maxWidth
      product.style.minWidth = productWidth
      product.style.maxWidth = productWidth
    }
  },
  methods: {
    swipeProducts(direction) {
      if (direction === 'previous' && this.distanceFromStart > 0) {
        this.distanceFromStart = this.distanceFromStart - this.productsSwiperWidth
      } else if (direction === 'next' && this.distanceFromStart < this.maxDistancePossible) {
        this.distanceFromStart = this.distanceFromStart + this.productsSwiperWidth
      }
      for (const product of Array.from(this.$refs.productsSwiper.children)) {
        product.style.transform = `translateX(-${this.distanceFromStart}px)`
      }
    },
    arrowDisabledStyle(side) {
      if (side === 'left') {
        return this.distanceFromStart === 0 ? 'filter: grayscale(100%) brightness(130%)' : ''
      } else {
        return this.distanceFromStart > this.maxDistancePossible ? 'filter: grayscale(100%) brightness(130%)' : ''
      }
    },
    priceVariationValue(product) {
      const priceVariation = Math.abs(product.price * product.percentage / 100)
      return priceVariation.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL', minimumFractionDigits: 0, maximumFractionDigits: 0 })
    },
    priceVariationTagStyle(product) {
      return { backgroundColor: product.color }
    },
    priceVariationArrowStyle(product) {
      if (Math.sign(product.price * product.percentage / 100) === 1) return 'transform: rotate(180deg)'
    },
    truncateTitle(product) {
      const maxTitleLength = 65
      const dots = product.title.length > maxTitleLength ? '...' : ''
      return product.title.substring(0, maxTitleLength) + dots
    },
    storeName(product) {
      const storeFound = this.stores.find(store => store.id === product.storeid)
      return storeFound.name
    }
  }
}
</script>

<style lang="scss" scoped>
.products-swiper-container {
  display: flex;
  align-items: center;
  justify-items: center;
  width: 100%;
  position: relative;
  .arrow {
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto;
    width: 45px;
    cursor: pointer;
    transition: cubic-bezier(0.455, 0.03, 0.515, 0.955) all .26s;
  }
  .arrow-previous {
    left: 0;
    transform: translateX(-150%) rotate(180deg);
  }
  .arrow-next {
    right: 0;
    transform: translateX(150%);
  }
  .products-swiper {
    display: flex;
    overflow: hidden;
    overflow-x: scroll;
    .product {
      position: relative;
      display: grid;
      grid-template-columns: 1fr;
      grid-template-rows: auto 1fr auto auto;
      margin: 10px;
      padding: 28px;
      border-radius: 15px;
      text-decoration: none;
      color: #454344;
      box-shadow: 1px 1px 8px 0px rgba(0,0,0,.1);
      transition: cubic-bezier(0.455, 0.03, 0.515, 0.955) all .26s;
      .price-variation-tag {
        display: flex;
        align-items: center;
        position: absolute;
        top: 15px;
        left: 0;
        background-color: green;
        border-radius: 0 8px 8px 0;
        padding: 7px;
        .price-variation-arrow {
          width: 12px;
          margin-right: 4px;
        }
        .price-variation-value {
          color: #fff;
          font-size: 13px;
          font-weight: 500;
        }
      }
      .product-image-link {
        display: flex;
        justify-content: center;
        .product-image {
          object-fit: contain;
        }
      }
      .product-title {
        text-align: center;
        font-size: 15px;
        font-weight: 500;
        text-decoration: none;
        color: #454344;
        margin: 35px 0;
      }
      .product-store {
        text-align: center;
        font-size: 14px;
        color: rgb(142,142,142);
        cursor: default;
        margin-bottom: 8px;
        .product-store-link {
          font-weight: 500;
          text-decoration: none;
          color: #3D92F5;
        }
      }
      .product-price {
        text-align: center;
        font-size: 20px;
        font-weight: 700;
        color: #2977CE;
        text-decoration: none;
      }
    }
    .product:hover {
      box-shadow: 1px 1px 12px 0px rgba(0,0,0,.2);
    }
  }
}
.see-more-button {
  outline: none;
  border: none;
  background-color: #2977CE;
  font-size: 16px;
  font-weight: 700;
  color: #fff;
  padding: 12px 22px;
  border-radius: 100px;
  box-shadow: 1px 1px 8px 0px rgba(0,0,0,.15);
  transition: cubic-bezier(0.455, 0.03, 0.515, 0.955) all .26s;
  cursor: pointer;
  margin-top: 25px;
}
.see-more-button:hover {
  background-color: #3D92F5;
  box-shadow: 1px 1px 12px 0px rgba(0,0,0,.15);
}
::-webkit-scrollbar {
  width: 0px;
  background: transparent;
}

@media only screen and (max-width: 480px) {
  .products-swiper-container {
    .arrow {
      display: none;
    }
  }
}
</style>
