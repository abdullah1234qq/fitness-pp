<script setup>
import Welcome from './components/pages/Welcome.vue';
import Layout from './components/layouts/Layout.vue';
import Dashboard from './components/pages/Dashboard.vue';
import Workout from "./components/pages/Workout.vue"
import { ref, computed } from 'vue';
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
const data = ref(defaultData)
const selectedWorkout = ref(1)
console.log(selectedWorkout.value)
const isWorkoutCompleted = computed(() => {
    const currWorkout = data.value?.[selectedWorkout.value]
    if (!currWorkout) return false
    const isCompletedCheck = Object.values(currWorkout).every(ex => !!ex)
    console.log("INCOMPLETE:", isCompletedCheck)
    return isCompletedCheck
})
const firstIncompleteWorkoutIndex = computed(() => {
    const allWorkouts = data.value
    if (!allWorkouts) return -1
    for (const [index, workout] of Object.entries(allWorkouts)) {
        const isCompleted = Object.values(workout).every(ex => !!ex)
        if (!isCompleted) {
            return parseInt(index)
        }
    }
    return -1
    return selectedDisplay.value = 2

})
function handleChangeDisplay(idx) {
    console.log('Changing display to:', idx)
    selectedDisplay.value = idx
}
function handleSelectWorkout(idx) {
    console.log('Selected workout:', idx)
    selectedWorkout.value = idx
    selectedDisplay.value = 3

}
function handleSaveWorkout() {
    localStorage.setItem('workouts', JSON.stringify(data.value))
    selectedDisplay.value = 2
    selectedWorkout.value = -1
}
</script>

<template>
    <Layout>
        <Welcome :handleChangeDisplay="handleChangeDisplay" v-if="selectedDisplay == 1" />
        <Dashboard :firstIncompleteWorkoutIndex="firstIncompleteWorkoutIndex" :handleSelectWorkout="handleSelectWorkout"
            v-if="selectedDisplay == 2" />
        <Workout :handleSaveWorkout="handleSaveWorkout" :isWorkoutCompleted="isWorkoutCompleted" :data="data"
            :selectedWorkout="selectedWorkout" v-if="workoutProgram?.[selectedWorkout]" />
    </Layout>
</template>

<style scoped></style>
