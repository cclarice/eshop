<template>
  <div class="EshopProductForm">
    <BaseInputText class="FormName"
                   header="Наименование товара"
                   :placeholder="'Введите наименование товара'"
                   :required="true"
                   @changeValue="changeValue('formName', $event)"
                   :autofocus="true"/>
    <BaseTextarea class="FormDescription"
                  header="Описание товара"
                  :placeholder="'Введите описание товара'"
                   @changeValue="changeValue('formDescription', $event)"/>
    <BaseInputText class="FormImageLink"
                   header="Ссылка на изображение товара"
                   :placeholder="'Введите ссылку'"
                   :required="true"
                   @changeValue="changeValue('formImage', $event)"/>
    <BaseInputText class="FormPrice"
                   header="Цена товара"
                   :placeholder="'Введите цену'"
                   :required="true"
                   :type="'number'"
                   @changeValue="changeValue('formPrice', $event)"/>
    <BaseButton class="FormAccept"
                text="Добавить товар"
                @clickButton="addProduct(formName, formDescription, formImage, formPrice)"
                :disabled="!valid"/>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'
import BaseInputText from "@/components/base/BaseInputText";
import BaseTextarea from "@/components/base/BaseTextarea";
import BaseButton from "@/components/base/BaseButton";

export default Vue.extend({
  name: 'ProductForm',
  components: { BaseInputText, BaseTextarea, BaseButton },
  data () {
    return {
      formName: '',
      formDescription: '',
      formImage: '',
      formPrice: 0,
      valid: false
    }
  },
  methods: {
    changeValue (valueName, toValue) {
      this[valueName] = toValue
      this.valid = (this.formName.length && this.formImage.length && this.formPrice)
    },
    addProduct (formName, formDescription, formImage, formPrice) {
      if (!formName || !formImage || !formPrice) {
        return // todo highlight errors
      }

      this.$emit('addProduct', {
        id: Date.now(),
        name: formName,
        description: formDescription,
        image: formImage,
        price: formPrice
      })
    }
  }
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