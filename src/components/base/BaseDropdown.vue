<template>
  <div class="BaseDropdownCont">
    <select class="BaseDropdown"
            :aria-disabled="!options.length"
            v-model="value"
            @change="changeValue">
      <option v-for="option in options"
              :key="option.name"
              :value="option.name"
              class="BaseDropdownOption">
        {{ option.text }}
      </option>
    </select>
    <label class="BaseDropdownLabel">
      <img src="../../assets/dropdown.svg" alt="">
    </label>
  </div>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseDropdown',
  data () {
    return ({
      value: ''
    })
  },
  props: {
    options: {
      type: Array,
      default: () => { return [] }
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
.BaseDropdownCont {
  z-index: 128000;
}
.BaseDropdown {
  z-index: 128000;
  height: 36px;
  background: #FFFEFB;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  outline: none;
  font-family: 'Source Sans Pro', sans-serif;
  padding: 10px 28px 9px 16px;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
  appearance: none;
  .BaseDropdownOption {
    appearance: none;
  }
}

.arrow {
  border: solid black;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;
}

.BaseDropdownLabel {
  position: absolute;
  transform: translate(calc(-100% - 16px), 9px);
}
</style>