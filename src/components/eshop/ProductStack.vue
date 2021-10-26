<template>
  <div class="ProductStack">
    <Product class="Product"
             v-for="(product, index) of products"
             :key="product.name + '_' + product.id"
             :index="index"
             :product="product"
             @removeProduct="removeProduct($event)"/>
    <Product class="Product"
             v-if="!products.length"
             :product="{
               id: -1,
               name: 'Добавьте продукт',
               description: '',
               image: 'products/imageAdd.png',
               price: -1
             }"
             @removeProduct="null"/>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'
import Product from "@/components/eshop/Product";

export default Vue.extend({
  name: 'ProductStack',
  components: { Product },
  props: {
    products: {
      type: Array,
      default: () => { return [] }
    }
  },
  methods: {
    removeProduct(productId) {
      this.$emit('removeProduct', productId)
    }
  }
})
</script>

<style scoped lang='scss'>
.ProductStack {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
}

.ProductStack > *:not(:nth-child(4n+4)) {
  margin-right: 16px;
}

@media (max-width: 1692px) {
  .ProductStack > *:not(:nth-child(3n+3)) {
    margin-right: 16px;
  }
  .ProductStack > *:nth-child(3n+3) {
    margin-right: 0;
  }
}

@media (max-width: 1360px) {
  .ProductStack > *:not(:nth-child(2n)) {
    margin-right: 16px;
  }
  .ProductStack > *:nth-child(2n) {
    margin-right: 0;
  }
}

@media (max-width: 1028px) {
  .ProductStack > * {
    margin-right: 0 !important;
  }
}

@media (max-width: 696px) {
  // Nothing
}
</style>