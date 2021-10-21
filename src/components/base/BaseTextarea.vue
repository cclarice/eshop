<template>
  <label class="BaseTextarea">
    <span class="BaseTextareaHeader" v-if="header">
      {{ header }}
      <img v-if="required" class="BaseTextareaRequired" src="../../assets/required.svg" alt="Required">
    </span>
    <textarea class="BaseTextareaText"
              :class="{hasError: hasError}">
    </textarea>
    <span class="BaseTextareaError"></span>
  </label>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseTextarea',
  data: {
    errorMessage: 'Поле является обязательным'
  },
  props: {
    header: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    },
    value: {
      type: String,
      default: ''
    },
    required: {
      type: Boolean,
      default: false
    },
    hasError: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    changeValue (value) {
      this.$emit('changeValue', value)
    },
    checkValue () {
      this.hasError = (this.required && this.value.length)
    }
  }
})
</script>

<style scoped lang='scss'>
.hasError {
  border-color: #FF8484
}
</style>