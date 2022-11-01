<template>
    <input 
        type="checkbox"
        :checked="modelValue" 
        @change="$emit('update.modelValue', $event.target.checked)"
         
    />
    <label class="ml-5 mt-2" v-if="label">{{ label }}</label>
</template>

<script>

export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        modelValue: {
            type: Boolean,
            default: false
        }
    }
}
</script>