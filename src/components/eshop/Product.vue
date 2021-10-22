<template>
  <div class="Product">
    <img :src="product.src" :alt="'Image of ' + 'name'">
  </div>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'Product'
})
</script>

<style scoped lang='scss'>
.Product {
  background: #FFFEFB;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  width: calc(33% - 16px * 0.33);
}

</style>