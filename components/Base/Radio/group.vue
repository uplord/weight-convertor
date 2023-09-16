<template>
  <div class="field">
    <div class="label" v-if="title">{{ title }}</div>
    <div class="input-wrap radio-group" :class="{ 'horizontal' : horizontal == 'true', 'radio-buttons' : buttons == 'true' }">
      <div class="radio"
        v-for="option in options"
        :key="option.value"
      >
        <BaseRadio
          :label="option.label"
          :value="option.value"
          :modelValue="option.modelValue ? option.modelValue : modelValue"
          :name="name"
          :id="option.id"
          :disabled="option.disabled"
          @update:modelValue="$emit('update:modelValue', $event)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    modelValue: {
      type: [String, Number],
      required: true
    },
    horizontal: {
      type: [String, Boolean],
      default: false
    },
    buttons: {
      type: [String, Boolean],
      default: false
    }
  }
}
</script>

<style lang="less" scoped>
  @import '../style';
  @import 'style';
</style>