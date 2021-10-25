<template>
  <label class="BaseInputText">
    <span class="BaseInputTextHeader" v-if="header">
      {{ header }}
      <img v-if="required" class="BaseInputTextRequired" src="../../assets/required.svg" alt="Required">
    </span>
    <input class="BaseInputTextText"
           :class="{ hasError: this.hasError }"
           :placeholder="placeholder"
           :type="type"
           @blur="checkValue"
           v-model="value"
           @input="changeValue(value)"/>
    <span class="BaseInputTextError" :class="{ hasError: this.hasError }">{{ errorMessage }}</span>
  </label>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseInputText',
  data () {
    return {
      errorMessage: 'Поле является обязательным',
      hasError: false,
      value: ''
    }
  },
  props: {
    type: {
      type: String,
      default: 'text'
    },
    header: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    },
    defaultValue: {
      type: String,
      default: ''
    },
    required: {
      type: Boolean,
      default: false
    },
    inputModeNumeric: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    changeValue (value) {
      console.log('TryChange to', value)
      this.$emit('changeValue', value)
      this.checkValue()
    },
    checkValue () {
      this.hasError = (this.required && !this.value.length)
    }
  }
})
</script>

<style scoped lang='scss'>
.BaseInputText {
  display: flex;
  flex-direction: column;
  margin-bottom: 2px;
  .BaseInputTextHeader {
    font-size: 10px;
    line-height: 13px;
    letter-spacing: -0.02em;
    color: #49485E;
    margin-bottom: 4px;

    display: flex;
    .BaseInputTextRequired {
      width: 4px;
      height: 4px;
    }
  }
  .BaseInputTextText {
    width: 100%;
    height: 36px;

    background: #FFFEFB;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;

    outline: none;
    border: none;
    padding: 10px 14px;

    font-size: 12px;
    line-height: 15px;
    color: #3F3F3F;
    &::placeholder {
      color: #B4B4B4;
    }
  }
  .BaseInputTextError {
    opacity: 0;
    margin-top: 4px;

    font-size: 8px;
    line-height: 10px;
    letter-spacing: -0.02em;
    color: #FF8484;
    font-weight: 400;
  }
}


.hasError {
  opacity: 1 !important;
  border-color: #FF8484;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type=number] {
  -moz-appearance: textfield;
}
</style>