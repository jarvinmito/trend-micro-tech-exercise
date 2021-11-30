<template>
    <div class="pass-input">
        <div class="pass-input__container">
            <div class="pass-input__toggler" @click="toggleShowPassword">
                <img v-if="!show_password" src="/view-off.svg" />
                <img v-else src="/view-on.svg" />
            </div>
            <TextInput v-model="computedValue" type="password" :label="label" />
            <div v-if="show_password" class="pass-input__shown">{{ computedValue }}</div>
        </div>
        <div class="pass-input__validation" :style="`opacity: ${hasValidPassword ? '1' : '0'};`">
            <div
                v-for="(criteria, cIndex) in criterias"
                :key="`validation-criteria-${cIndex}`"
                class="pass-input__validation__item"
            >
                <img :src="`/validation-${criteria.value ? '' : 'in'}active.svg`" />
                {{ criteria.text }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['value', 'label'],
    computed: {
        computedValue: {
            get () { return this.value },
            set (val) { this.$emit('input', val) }
        },
        hasValidPassword () {
            return this.criterias.findIndex(c => c.value) !== -1
        }
    },
    watch: {
        computedValue (value) {
            this.resetCriteriaValidation()
            // Min chars of 8
            if (value.length >= 8) {
                this.validate('min-chars')
            }
            // has one number
            if (/\d/.test(String(value))) {
                this.validate('num')
            }
        }
    },
    data () {
        return {
            show_password: false,
            criterias: [
                { name: 'min-chars', text: '8 Characters min.', value: false },
                { name: 'num', text: 'One number', value: false }
            ]
        }
    },
    methods: {
        resetCriteriaValidation () {
            this.criterias.map(c => {
                c.value = false
            })
        },
        validate (criteria_name) {
            this.criterias.map(c => {
                if (c.name === criteria_name) c.value = true
            })
        },
        toggleShowPassword () {
            this.show_password = !this.show_password
        }
    }
}
</script>

<style lang="scss" scoped>
.pass-input {
    &__container {
        position: relative;
    }
    &__toggler {
        position: absolute;
        right: 2rem;
        top: 1.55rem;
        z-index: 12;
        width: 2.4rem;
        height: 2.4rem;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
    }
    &__shown {
        position: absolute;
        left: 0.8rem;
        bottom: 0.8rem;
        font-size: 1rem;
    }

    &__validation {
        gap: 1.2rem;
        margin-top: 0.5rem;
        &,
        &__item {
            display: flex;
            flex-direction: row;
            justify-content: flex-start;
            align-items: center;
        }

        &__item { gap: 0.5rem; }
    }
}
</style>