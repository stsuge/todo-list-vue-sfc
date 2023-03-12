<template>
    <fieldset>
        <label v-for="option in options" :key="option.value">
            <input type="radio" v-bind:value="option.value" v-bind:checked="option.value == modelValue"
                v-on:change="updateValue">
            {{ option.label }}
        </label>
    </fieldset>
</template>

<script>
export default {
    props: {
        modelValue: { type: Number, require: true, default: -1 },
        options: { type: Array, require: true, default: [] },
        name: { type: String, require: true, default: '' }
    },
    emits: ['update:modelValue'],
    methods: {
        updateValue: function (e) {
            this.$emit('update:modelValue', Number(e.target.value))
        }
    }
}
</script>