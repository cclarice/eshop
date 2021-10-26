<template>
  <label class="BaseTextarea">
    <span class="BaseTextareaHeader" v-if="header">
      {{ header }}
      <img v-if="required" class="BaseTextareaRequired" src="../../assets/required.svg" alt="Required">
    </span>
    <textarea class="BaseTextareaText"
              :class="{hasError: hasError}"
              :placeholder="placeholder">
    </textarea>
    <!-- Unused <span class="BaseTextareaError"> {{ hasError ? errorMessage : '' }} </span> -->
  </label>
</template>

<script lang='js'>
import Vue from 'vue'

export default Vue.extend({
  name: 'BaseTextarea',
  data () {
    return {
      errorMessage: 'Поле является обязательным',
      hasError: false
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
    }/* ,
    hasError: {
      type: Boolean,
      default: false
    } */
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
.BaseTextarea {
  display: flex;
  flex-direction: column;
  margin-bottom: 14px;
  .BaseTextareaHeader {
    font-size: 10px;
    line-height: 13px;
    letter-spacing: -0.02em;
    color: #49485E;
    margin-bottom: 4px;
  }
  .BaseTextareaText {
    width: 100%;
    height: 108px;
    resize: none;

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
.invisible {
  opacity: 0;
  pointer-events: none;
  user-select: none;
}

</style>