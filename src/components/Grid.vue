<script setup>
import { workoutProgram } from "../utils/next.js"
const workoutTypes = ["push", "pull", "legs"]
defineProps({
    handleSelectWorkout: Function
})
</script>
<template>
    <section id="grid">
        <button @click="handleSelectWorkout(workoutIdx)" :key="workoutIdx"
            v-for="(workout, workoutIdx) in Object.keys(workoutProgram)" class="card-button plan-card">
            <div class="">
                <p>Day {{ workoutIdx < 9 ? "0" + (workoutIdx + 1) : workoutIdx + 1 }}</p>

                        <i class="fa-solid fa-dumbbell" v-if="workoutIdx % 3 == 0"></i>
                        <i class="fa-solid fa-weight-hanging" v-if="workoutIdx % 3 == 1"></i>
                        <i class="fa-solid fa-bolt" v-if="workoutIdx % 3 == 2"></i>

            </div>
            <h3>{{ workoutTypes[workoutIdx % 3] }}</h3>
        </button>
    </section>
</template>
<style scoped>
#grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 1rem;
}

#grid button {
    width: 100%;
}

.plan-card {
    display: flex;
    flex-direction: column;
}

.plan-card div {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
}
</style>