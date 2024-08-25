<script setup lang="ts">
import { computed, reactive, ref, type ComputedRef } from 'vue';
import Test from './components/test.vue';
import RecommendTest from './components/recommendTest.vue';
import TestInterfaceWithProps from './components/testInterfaceWithProps.vue';
import TestWithDefaultValues from './components/TestWithDefaultValues.vue';
import TestWithEmit from './components/TestWithEmit.vue';

const count = ref<number | string>('150');

interface Dreams {
    id: number;
    name: string;
    dream: string;
}

const persons = reactive<Dreams[]>([
    {
        id: 1,
        name: 'Cristiano',
        dream: 'To be a soccer player',
    },
    {
        id: 2,
        name: 'Erisvaldo',
        dream: 'Also to be a soccer player',
    },
    {
        id: 3,
        name: 'Davi',
        dream: 'Maybe one day to be a soccer player too',
    },
]);

const dreams = reactive<(string | number | object)[]>([
    'Doctor',
    'Soccer player',
    'Laywer',
    30,
    { heyy: 'example' },
]);

const explicitDreamGenerator: ComputedRef<string> = computed(
    () => 'This is your dream more explicit.'
);
const dreamGenerator = computed<string>(() => 'This is your dream.');

function captureFocus(event: Event) {
    const input = (event.target as HTMLInputElement);
    const numericValue = isNaN(Number(input.value)) ? input.value : Number(input.value);
    const result: string | number = numericValue;
    console.log(result);
}

function showUser(name: string) {
    console.log(name);
}

function write(event: Event) {

    if(event.target) {
        const input = event.target as HTMLInputElement;
        console.log(input.value);
    }
   
}

</script>

<template>
    <ul>
        <li v-for="person in persons">
            {{ person.name }} - {{ person.dream }}
        </li>
    </ul>

    <ul>
        <li v-for="dream in dreams">
            {{ dream }}
        </li>
    </ul>

    {{ dreamGenerator }} - {{ explicitDreamGenerator }}

    <input type="text" name="test" id="test" @focus="captureFocus" />

    <Test message="Hey, i'm testing."/>
    <Test message="Hey, i'm testing." warning="Now with warning value"/>
    <RecommendTest user="cris06@outlook.com" purpose="Catch up greather strength"/>
    <TestInterfaceWithProps :allowed="true" :data="['LaidesMan127', 'user@test.com']"/>
    <TestInterfaceWithProps :allowed="false"/>
    <TestWithDefaultValues last-name="123"/>
    <TestWithEmit @sent="showUser" @inputEvent="write"/>

    <!-- <button @click="count += 15"> Increase </button> -->
</template>

<style scoped></style>