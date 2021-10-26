<template>
  <div class="Product"
       @mouseenter="removeSetVisibility(true)"
       @mouseleave="removeSetVisibility(false)"
       :style="{animationDelay: index / 10 + 's', zIndex: 65536 - index}"
       :id="'product' + index">
    <div v-if="this.removeVisible" class="ProductRemovePosition">
      <div class="ProductRemove"
           :class="{ProductRemoveVisible: this.removeVisible}"
           @click="removeProduct"/>
    </div>
    <div class="ProductImageContainer">
      <img class="ProductImage"
           :src="product.image"
           :alt="'Image of ' + product.name"/>
    </div>
<!--    <div class="ProductImage"-->
<!--         :style="{ backgroundImage: 'url(' +  product.image + ')' }"/>-->
    <h3 class="ProductHeader">
      {{ product.name }}
    </h3>
    <p class="ProductDescription">
      {{ product.description }}
    </p>
    <h2 class="ProductPrice">
      {{ formatPrice !== '-1' ? formatPrice + '₽' : '-'}}
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
      default: () => { return {} }
    },
    index: {
      type: Number,
      default: 0
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
        if (!((priceString.length - i - 1) % 3)) {
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
  },
  mounted () {
    setTimeout(() => {document.getElementById('product' + this.index).style.opacity = '1'}, this.index * 100 + 50)
  }
})
</script>

<style scoped lang='scss'>
.Product {
  background: #FFFEFB;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  width: calc(25% - 16px * 0.75);
  margin-bottom: 16px;

  display: flex;
  flex-direction: column;
  height: 423px;
  animation: ease productAppear 1s;
  transition-duration: 175ms;
  transform: scale(1) translateY(0);
  opacity: 0;
  &:hover {
    transform: scale(1.025) translateY(1.25%);
    z-index: 10;
  }
  .ProductImageContainer {
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 4px 4px 0 0;

    width: 100%;
    height: 47.28%;
    z-index: 5;
    .ProductImage {
      display: flex;
      position: relative;
      object-fit: cover;
      width: 100%;
      height: 100%;
      border-radius: 4px 4px 0 0;
      &:before {
        content: ' ';
        position: absolute;
        display: block;
        height: 100%;
        width: 100%;
        border-radius: 4px 4px 0 0;
        background-image: url('../../assets/imageNotFound.png');
        background-size: contain;
        background-position: center;
        background-repeat: no-repeat;
        background-color: #DBDAE0;
      }
    }
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

@keyframes productAppear {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.ProductRemoving {
  animation: ease productRemoving 500ms;
}

@keyframes productRemoving {
  from {
    transform: scale(1);
  }
  50% {
    transform: scale(0);
  }
  to {
    transform: scale(0);
  }
}

@media (max-width: 1692px) {
  .Product {
    width: calc(33.3333% - 16px * 0.6666);
  }
}

@media (max-width: 1360px) {
  .Product {
    width: calc(50% - 16px * 0.5);
  }
}

@media (max-width: 1028px) {
  .Product {
    width: calc(100%);
  }
}

@media (max-width: 696px) {

}
</style>