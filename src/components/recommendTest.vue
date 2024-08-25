<template>
    {{ propsNotRecommended.user }} - {{ propsNotRecommended.purpose }} <br />
</template>

<script setup lang="ts">

const propsNotRecommended = defineProps<{
    user: string,
    purpose: string, 
}>();


</script>

<style lang="sass"></style>