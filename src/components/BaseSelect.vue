<template>
    <label>{{ label }}</label>
    <br/>
    <select 
        :value="modelValue"
        class="border form-control w-full p-2 my-3 text-black"
        v-bind="{
            ...$attrs,
            onChange: ($event) => {$emit('update:modelValue',$event.target.value )}
        }"
    >
        <option
          v-for="option in options"
          :key="option"
          :value="option"
          :selected="option === modelValue"
        >{{ option }}</option>
      </select>
</template>

<script>
export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        modelValue: {
            type: [String, Number],
            default: ''
        },
        options: {
            type: Array,
            required: true
        }
    }
}
</script>