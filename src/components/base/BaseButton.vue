<template>
  <button class="BaseButton"
          @click="clickButton"
          :disabled="disabled">
    {{ text }}
  </button>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseButton',
  props: {
    text: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    clickButton () {
      this.$emit('clickButton')
    }
  }
})
</script>

<style scoped lang='scss'>
.BaseButton {
  width: 100%;
  height: 36px;
  border-radius: 10px;
  border: none;
  outline: none;

  color: #FFFFFF;
  background: #7BAE73;

  font-size: 12px;
  font-weight: 600;
  font-family: Inter, sans-serif !important;
  &:disabled {
    background: #EEEEEE;
    color: #B4B4B4;
  }
}


</style>