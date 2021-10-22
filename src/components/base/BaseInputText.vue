<template>
  <label class="BaseInputText">
    <span class="BaseInputTextHeader" v-if="header">
      {{ header }}
      <img v-if="required" class="BaseInputTextRequired" src="../../assets/required.svg" alt="Required">
    </span>
    <input class="BaseInputTextText"
           :class="{hasError: hasError}"
           :placeholder="placeholder"
           type="text">
    <span class="BaseInputTextError">{{ errorMessage }}</span>
  </label>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseInputText',
  data () {
    return {
      errorMessage: 'Поле является обязательным'
    }
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
    margin-top: 4px;

    font-size: 8px;
    line-height: 10px;
    letter-spacing: -0.02em;
    color: #FF8484;
    font-weight: 400;
  }
}


.hasError {
  border-color: #FF8484
}
</style>