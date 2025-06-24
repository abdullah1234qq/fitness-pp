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
            <div class="workout-grid" v-for="(w, wIdx) in workout" key="wIdx">
                <div class="grid-name">
                    <p>{{ w.name }}</p>
                    <button>
                        <i class="fa-regular fa-circle-question"></i>
                    </button>
                </div>
                <p>{{ w.sets }}</p>
                <p>{{ w.reps }}</p>
                <input type="text" placeholder="14kg" class="grid-weight" v-model="w.weight">
            </div>
            <br />
            <div class="workout-grid-line">
                <h4 class="grid-name">Workout</h4>
                <h6>Sets</h6>
                <h6>Reps</h6>
                <h6 class="grid-weight">Weight</h6>
                <div class="workout-grid" v-for="(w, wIdx) in workout" key="wIdx">
                    <div class="grid-name">
                        <p>{{ w.name }}</p>
                        <button>
                            <i class="fa-regular fa-circle-question"></i>
                        </button>
                    </div>
                    <p>{{ w.sets }}</p>
                    <p>{{ w.reps }}</p>
                    <input type="text" placeholder="14kg" class="grid-weight">
                </div>
                <br />

                <div class="card"><button>Save and Exit <i class="fa-solid fa-save"></i></button></div>
            </div>
        </div>
    </section>
</template>
<style scoped></style>