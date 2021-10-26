<template>
  <label class="BaseInputText">
    <span class="BaseInputTextHeader" v-if="header">
      {{ header }}
      <img v-if="required" class="BaseInputTextRequired" src="../../assets/required.svg" alt="Required">
    </span>
    <input class="BaseInputTextText"
           :class="{ hasErrorInput: this.hasError }"
           :placeholder="placeholder"
           :type="type"
           @blur="checkValue"
           v-model="value"
           @input="changeValue(value)"
           :autofocus="autofocus"/>
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
    },
    autofocus: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    changeValue (value) {
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
    &:hover {
      border-bottom: #7B7B7366 solid 1px;
      padding-bottom: 9px;
    }
    &:active, &:focus {
      border-bottom: #7BAE73 solid 1px;
      padding-bottom: 9px;
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
}
.hasErrorInput {
  border: #FF8484 solid 1px !important;
  padding: 9px 13px !important;
  &:focus {
    box-shadow: 0 0 8px 2px #FF8484;
  }
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