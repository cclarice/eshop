<template>
  <label class="BaseTextarea">
    <span class="BaseTextareaHeader" v-if="header">
      {{ header }}
      <img v-if="required" class="BaseTextareaRequired" src="../../assets/required.svg" alt="Required">
    </span>
    <textarea class="BaseTextareaText"
              :class="{hasError: hasError}">
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
  }
}
.hasError {
  border-color: #FF8484
}
.invisible {
  opacity: 0;
  pointer-events: none;
  user-select: none;
}
</style>