<template>
  <div class="EshopProductForm">
    <BaseInputText class="FormName"
                   header="Наименование товара"
                   :placeholder="'Введите наименование товара'"
                   :required="true"/>
    <BaseTextarea class="FormDescription"
                  header="Описание товара"
                  :placeholder="'Введите описание товара'"/>
    <BaseInputText class="FormImageLink"
                   header="Ссылка на изображение товара"
                   :placeholder="'Введите ссылку'"
                   :required="true"/>
    <BaseInputText class="FormPrice"
                   header="Цена товара"
                   :placeholder="'Введите цену'"
                   :required="true"/>
    <BaseButton class="FormAccept"
                text="Добавить товар"/>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'
import BaseInputText from "@/components/base/BaseInputText";
import BaseTextarea from "@/components/base/BaseTextarea";
import BaseButton from "@/components/base/BaseButton";

export default Vue.extend({
  name: 'ProductForm',
  components: { BaseInputText, BaseTextarea, BaseButton }
})
</script>

<style scoped lang='scss'>
.EshopProductForm {
  display: flex;
  flex-direction: column;
  .FormAccept {
    margin-top: 10px;
  }
  .BaseInputText {
    max-height: 67px;
  }
}
</style>