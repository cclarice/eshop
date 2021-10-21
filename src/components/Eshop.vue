<template>
  <div class="Eshop">
    <header class="EshopHeader">
      <h1></h1>
      <BaseDropdown/>
    </header>
    <main class="EshopMain">
      <ProductForm/>
      <ProductStack/>
    </main>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'
import ProductStack from "@/components/eshop/ProductStack";
import ProductForm from "@/components/eshop/ProductForm";
import BaseDropdown from "@/components/base/BaseDropdown";

export default Vue.extend({
  name: 'Eshop',
  components: {BaseDropdown, ProductForm, ProductStack }
})
</script>

<style scoped lang='scss'>

</style>