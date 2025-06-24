<script setup>
import { workoutProgram } from "../../utils/next.js";
const selectedWorkout = 4
const { workout = [], warmup = [] } = workoutProgram[selectedWorkout] || {};
</script>
<template>
    <section id="workout-card">
        <div class="plan-card card">
            <div class="plan-card-header">
                <p>Day {{ selectedWorkout < 10 ? "0" + selectedWorkout : selectedWorkout }}</p>
                        <i class="fa-solid fa-dumbbell"></i>
            </div>
            <h2>{{ 'push' }} Workout </h2>
        </div>
        <div class="workout-grid">
            <h4 class="grid-name">Warmup</h4>
            <h6>Sets</h6>
            <h6>Reps</h6>
            <h6 class="grid-weight">Weight</h6>
            <div class="workout-grid" v-for="(w, wIdx) in warmup" key="wIdx">
                {{ w.name }}
            </div>
        </div>
    </section>
</template>
<style scoped></style>