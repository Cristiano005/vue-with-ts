<template>
    
{{ propsNotRecommended.message }} - {{ propsNotRecommended.warning }} <br>

</template>

<script setup lang="ts">

const propsNotRecommended = defineProps({
    message: {
        required: true,
        type: String,
    },
    warning: String, // could be String as Undefined, because wasn't declared the prop 'required' like 'true'.
})

</script>

<style lang="sass">
    
</style>