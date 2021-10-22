<template>
  <div class="Product"
       @mouseenter="removeSetVisibility(true)"
       @mouseleave="removeSetVisibility(false)">
    <div v-if="this.removeVisible" class="ProductRemovePosition">
      <div class="ProductRemove"
           :class="{ProductRemoveVisible: this.removeVisible}"
           @click="removeProduct"/>
    </div>
    <div class="ProductImage"
         :style="{ backgroundImage: 'url(' +  product.image + ')' }"/>
    <h3 class="ProductHeader">
      {{ product.name }}
    </h3>
    <p class="ProductDescription">
      {{ product.description }}
    </p>
    <h2 class="ProductPrice">
      {{ formatPrice }} ₽
    </h2>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'Product',
  data () {
    return {
      removeVisible: false
    }
  },
  props: {
    product: {
      type: Object,
      default: {}
    }
  },
  computed: {
    formatPrice () {
      if (!this.product) {
        return ''
      }

      const priceString = this.product.price.toString()
      let   price       = '' + priceString[priceString.length - 1]

      for (let i = priceString.length - 2; i >= 0; i--) {
        if (!((i + 1) % 3)) {
          price = ' ' + price
        }
        price = priceString[i] + price
      }
      return price;
    }
  },
  methods: {
    removeProduct() {
      this.$emit('removeProduct', this.product.id)
    },
    removeSetVisibility (visible) {
      this.removeVisible = visible
    }
  }
})
</script>

<style scoped lang='scss'>
.Product {
  background: #FFFEFB;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  width: calc(33.3333% - 16px * 0.6666);
  margin-bottom: 16px;

  display: flex;
  flex-direction: column;
  height: 423px;
  .ProductImage {
    border-radius: 4px 4px 0 0;

    width: 100%;
    padding: 30.125% 0;
    background-color: #DBDAE0;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    z-index: 5;
  }
  .ProductHeader {
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
    padding: 16px;
  }
  .ProductDescription {
    height: 100px;
    font-size: 16px;
    line-height: 20px;
    padding: 0 16px;
    margin-bottom: 12px;
  }
  .ProductPrice {
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
    padding: 0 16px;
  }


  // Remove Button
  &:hover {
    z-index: 10;
  }
  .ProductRemovePosition {
    display: flex;
    flex-direction: row-reverse;
    height: 0;
    max-height: 0;
    .ProductRemove {
      width: 32px;
      height: 32px;
      position: sticky;
      background-image: url("../../assets/remove.svg");
      z-index: 11;
      transform: translate(25%, -25%);
      animation: ease removeAppear 0.5s;
    }
  }

}

@keyframes removeAppear {
  from {
    transform: scale(0) translate(25%, -25%);
  }
  to {
    transform: scale(1) translate(25%, -25%);
  }
}
</style>