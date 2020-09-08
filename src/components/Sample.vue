<template>
    <p>{{ message }}{{ number }}</p>
</template>

<script>
export default {
    // 引数っぽい
    props: {
        message: {
            type: String,
            required: true,
            validator(value) {
                value.length <= 10
            }
        },
        number: {
            type: Number,
            default: 1 
        }
    }
}
</script>