<template>
    <div class="text-input" :class="{ 'text-input--focused': focused }">
        <label class="text-input__label">{{ placeholder || label || 'Text' }}</label>
        <input class="text-input__textbox" :type="type" v-model="computedValue" @focus="onFocus" @blur="onBlur" />
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: String,
            required: true
        },
        type: {
            type: String,
            default: 'text'
        },
        placeholder: {
            type: String,
            default: ''
        },
        label: {
            type: String,
            default: ''
        }
    },
    computed: {
        computedValue: {
            get () { return this.value },
            set (val) { this.$emit('input', val) }
        }
    },
    methods: {
        onFocus () {
            console.log('yes')
            this.focused = true
        },
        onBlur () {
            if (!this.computedValue.trim()) this.focused = false
        }
    },
    data () {
        return {
            focused: false
        }
    }
}
</script>

<style lang="scss" scoped>
.text-input {
    position: relative;
    width: 100%;
    background-color: var(--color-gray-light);
    &__label {
        position: absolute;
        top: 1.55rem;
        left: 0;
        padding: 0.5rem 0.8rem;
        font-size: 1.4rem;
        color: var(--color-gray-dark);
        transition: all 0.1s ease-in-out;
        
        .text-input--focused & {
            top: 0;
            font-size: 1.2rem;
        }
    }

    &__textbox {
        position: relative;
        z-index: 9;
        width: 100%;
        height: 5.5rem;
        padding: 1.4rem 0.8rem 0.5rem 0.8rem;
        font-size: 1.4rem;
        background: transparent;
        border: none;
        border-radius: 0.5rem;

        &.focus-visible {
            outline: none;
        }
    }
}
</style>