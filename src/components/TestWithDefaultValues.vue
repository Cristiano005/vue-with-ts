<template>
    {{ propsNotRecommended.firstName }} - {{ propsNotRecommended.lastName }} : {{ propsNotRecommended.age }} <br />
</template>

<script setup lang="ts">

interface User {
    firstName?: string,
    lastName?: string,
    age?: number,
}

const propsNotRecommended = withDefaults(defineProps<User>(), {
    firstName: "User",
    age: 18,
});

</script>

<style lang="sass"></style>