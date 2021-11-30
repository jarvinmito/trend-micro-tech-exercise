<template>
    <label class="check-input" :class="{ 'check-input--checked': computedValue }">
        <img v-if="computedValue" src="/tick.svg" class="check-input__icon" />
        <input type="checkbox" v-model="computedValue" />
    </label>
</template>

<script>
export default {
    props: ['value'],
    computed: {
        computedValue: {
            get () { return this.value },
            set (val) { this.$emit('input', val) }
        }
    }
}
</script>

<style lang="scss" scoped>
.check-input {
    position: relative;
    display: flex;
    width: 1.8rem;
    height: 1.8rem;
    background: var(--color-gray);
    border: 0.2rem solid var(--color-gray);
    border-radius: 0.5rem;
    cursor: pointer;
    & > input {
        position: absolute;
        opacity: 0;
        z-index: -1;
    }

    &__icon {
        position: absolute;
        bottom: 0.2rem;
        left: 0.2rem;
        height: 1.6rem;
    }

    &--checked {
        background: var(--color-white);
        border-color: var(--color-black);
    }
}
</style>