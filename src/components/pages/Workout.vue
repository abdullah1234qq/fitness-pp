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
            <div class="workout-grid">
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
                    <input type="text" placeholder="14kg" class="grid-weight" v-model="w.weight">
                </div>
            </div>
        </div>
    </section>
</template>
<style scoped>
#workout-card,
.plan-card {
    display: flex;
    flex-direction: column;

}

#workout-card {
    gap: 1.5rem;
}

.plan-card-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
}

.workout-grid,
.workout-grid-row {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    gap: 1rem;
}

.workout-grid,
.workout-grid-line {
    grid-column: span 7 / span 7;
    gap: 1 rem;
}

.grid-name {
    grid-column: span 3 / span 3;
}

.grid-name button {
    padding: 0;
    border: none;
    box-shadow: none;
}

.grid-name button:hover {
    transform: none;
    box-shadow: none;
    color: var(--color-link)
}
</style>