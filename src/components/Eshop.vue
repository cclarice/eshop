<template>
  <div class="Eshop">
    <header class="EshopHeader">
      <h1>Добавление товара</h1>
      <BaseDropdown/>
    </header>
    <main class="EshopMain">
      <ProductForm class="EshopProductForm"/>
      <ProductStack class="EshopProductStack"/>
    </main>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'
import BaseDropdown from "@/components/base/BaseDropdown";
import ProductForm from "@/components/eshop/ProductForm";
import ProductStack from "@/components/eshop/ProductStack";

export default Vue.extend({
  name: 'Eshop',
  components: { BaseDropdown, ProductForm, ProductStack }
})
</script>

<style scoped lang='scss'>
.Eshop {
  padding: 32px;
  .EshopHeader {
    width: 100%;
    height: 36px;

    display: flex;
    justify-content: space-between;
  }
  .EshopMain {
    margin-top: 16px;
    width: 100%;
    height: auto;

    display: flex;
    justify-content: space-between;

    h1 {
      font-weight: 600;
      font-size: 28px;
      line-height: 36px;
    }
    .EshopProductForm {
      width: calc(25% - 16px * 0.75);
      height: 440px; // todo: delete this

      box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);

      background-color: #FFFEFB;
      border-radius: 4px;
      padding: 24px;
    }
    .EshopProductStack {
      width: calc(75% - 16px * 0.25);

    }
  }
}

</style>