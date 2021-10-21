<template>
  <select class="BaseDropdown"
          :aria-disabled="!options.length"
          :v-model="value"
          @change="changeValue">
    <option v-for="option in options" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseDropdown',
  props: {
    options: {
      type: Array,
      default: []
    },
    value: {
      type: String,
      default: ''
    }
  },
  methods: {
    changeValue () {
      this.$emit('changeValue', this.value)
    }
  }
})
</script>

<style scoped lang='scss'>
</style>