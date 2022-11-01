<template>
  <br/>
  <label class="">{{ label }}</label>
  <br/>
  <input
    :placeholder="label"
    :value="modelValue"
    v-bind="$attrs"
    class="form-control w-full border p-2 rounded-md mt-3"
    @input="$emit('update:modelValue', $event.target.value)"
  />
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
  }
};
</script>