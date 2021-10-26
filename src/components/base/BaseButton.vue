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
  transition-duration: 100ms;
  &:hover {
    background: #6ca966;
    box-shadow: 0 0 4px 2px rgba(88, 203, 72, 0.23);
  }
  &:active {
    background: #63b65a;
    box-shadow: 0 0 6px 3px rgba(81, 210, 63, 0.32);
  }
  &:disabled {
    background: #EEEEEE;
    color: #B4B4B4;
  }
}


</style>