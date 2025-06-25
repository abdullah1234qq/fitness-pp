<script setup>
import Welcome from './components/pages/Welcome.vue';
import Layout from './components/layouts/Layout.vue';
import Dashboard from './components/pages/Dashboard.vue';
import Workout from "./components/pages/Workout.vue"
import { ref } from 'vue';
import { workoutProgram } from './utils/next';



const defaultData = {}
for (let workoutIdx in workoutProgram) {
    const workoutData = workoutProgram[workoutIdx]
    defaultData[workoutIdx] = {}

    for (let e of workoutData.workout) {
        defaultData[workoutIdx][e.name] = ''
    }
}
console.log(defaultData)

const selectedDisplay = ref(1)
const data = ref()
const selectedWorkout = ref(2)
function handleChangeDisplay(idx) {
    selectedDisplay.value = idx
}
function handleSelectWorkout(idx) {
    selectedDisplay.value = 3

    selectedWorkout.value = idx
    if (!data.value) {
        data.value = defaultData
    }
}
</script>

<template>
    <Layout>
        <Welcome v-if="selectedDisplay == 1" />
        <Dashboard v-if="selectedDisplay == 2" />
        <Workout :data="data" :selectedWorkout="selectedWorkout" v-if="workoutProgram?.[selectedWorkout]" />
    </Layout>
</template>

<style scoped></style>
