<template>
  <div class="EshopProductForm">
    <BaseInputText class="FormName"/>
    <BaseTextarea class="FormDescription"/>
    <BaseInputText class="FormImageLink"/>
    <BaseInputText class="FormPrice"/>
    <BaseButton class="FormAccept"/>
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

</style>