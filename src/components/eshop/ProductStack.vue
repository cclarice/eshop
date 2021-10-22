<template>
  <div class="ProductStack">
    <Product class="Product"
             v-for="product of products"
             :product="product"
             @removeProduct="removeProduct($event)"/>
    <Product class="Product"
             v-if="!products.length"
             :product="{}"
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
      default: []
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
  & > *:not(:nth-child(3n+3)) {
    margin-right: 16px;
  }
}
</style>