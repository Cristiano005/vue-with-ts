<template>
    <input type="text" placeholder="teste with emit inputEvent" @input="$emit('inputEvent', $event)">
    <button @click="$emit('sent', 'Cris')"> Click here! </button>
</template>

<script setup lang="ts">

interface User {
    firstName?: string,
    lastName?: string,
    age?: number,
}

const emits = defineEmits<{
    (e: 'inputEvent', event: Event): void,
    (e: 'sent', name: string): void,
}>();

</script>

<style lang="sass"></style>