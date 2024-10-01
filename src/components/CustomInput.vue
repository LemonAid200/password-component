<template>
    <div class="custom_input">
        <label for="">{{ label }}</label>
        <div class="custom_input__inner">
            <input :type="inputType" inert placeholder="password" v-model="value">
            <button @click="toggleInputType">Show</button>
        </div>        
    </div>
</template>
<script>

export default {
    name: 'CustomInput',
    props: {
        modelValue: {
            type:String,
            default: ''
        },

        label: {
            type: String,
            default: 'Enter admin password'
        }
    },
    data() {
        return {
            inputType:  'password'
        }
    },

    computed: {
        value: {
        get() {
            return this.modelValue
        },
        set(value) {
            this.$emit('update:modelValue', value)
        }
        }
    },

    methods: {
        toggleInputType(){
            this.inputType = this.inputType === 'password' ? 'text' : 'password'
        }
    }
    
}
</script>
<style scoped lang="scss">

.custom_input {
    background: white;
    border-radius: 20px;
    padding: 16px;
    text-align: left;

    label {
        font-size: small;
        display: block;
        margin-bottom: 16px;
    }

    &__inner {
        display: flex;
        justify-content: space-between;
        width: 100%;

        input {
            border: none;
            letter-spacing: 8px;
            font-size: larger;
            margin-right: 1px;
            flex-shrink: 1;
            width: 100%;
        }

        button {
            display: block;
            border: none;
            cursor: pointer;
            background: none;
            text-decoration: underline;
            font-size: medium;
            width: 52px;
        }
    }
}
    
</style>