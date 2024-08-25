<template>
    {{ propsNotRecommended.allowed }} - {{ propsNotRecommended.data }} <br />
</template>

<script setup lang="ts">

interface Props {
    allowed: boolean,
    data?: string[],
}

const propsNotRecommended = defineProps<Props>();

</script>

<style lang="sass"></style>