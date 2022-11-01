<template>
  <input
    type="radio"
    :value="value"
    v-bind="$attrs"
    :checked="modelValue === value"
    @change="$emit('update.modelValue', value)"
  />
  <label class="ml-3 mt-3" v-if="label">{{ label }}</label>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: "",
    },

    modelValue: {
      type: [String, Number],
      default: "",
    },

    value: {
      type: [String, Number],
      required: true,
    }
  }
}
</script>