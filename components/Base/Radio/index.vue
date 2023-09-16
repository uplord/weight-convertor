<template>
  <div class="field">
    <label v-if="title">{{ title }}</label>
    <div class="input-wrap radio-group">
      <div class="radio">
        <input
          type="radio"
          :checked="modelValue === value"
          :id="id"
          :disabled="disabled == 'true' || disabled == true"
          :value="value"
          v-bind="$attrs"
          @change="$emit('update:modelValue', value)"
        />
        <label v-if="label" :for="id">{{ label }}</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    id: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    },
    modelValue: {
      type: [String, Number],
      default: ''
    },
    value: {
      type: [String, Number],
      required: true
    }
  }
}
</script>

<style lang="less" scoped>
  @import '../style';
  @import 'style';
</style>