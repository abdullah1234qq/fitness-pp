<script setup>
const props = defineProps({
    selectedWorkout: Number,
    data: Object,
    handleSaveWorkout: Function,
    isWorkoutCompleted: Boolean
});
import Portal from "../Portal.vue";
import { workoutProgram, exerciseDescriptions } from "../../utils/next.js";
import { ref, computed } from "vue";
const workoutType = ['Push',
    'Pull',
    'Legs',];
const { workout = [], warmup = [] } = workoutProgram[props.selectedWorkout] || {};
console.log(props.selectedWorkout, workout, warmup);
const selectedExercise = ref(null)
// ...existing code...
const exerciseDescription = computed(() => exerciseDescriptions[selectedExercise.value] || {});
function handleCloseModal() {
    selectedExercise.value = null;
}
</script>
<template>
    <Portal hello="world" :handleCloseModal="handleCloseModal" v-if="selectedExercise">
        <div class="exercise-description">
            <h3>{{ selectedExercise }}</h3>
            <div>
                <small>
                    Description
                </small>
                <p>{{ exerciseDescription }}</p>
            </div>
            <button @click="handleCloseModal">Close <i class="fa-solid fa-xmark"></i></button>
        </div>
    </Portal>
    <section id="workout-card">
        <div class="plan-card card">
            <div class="plan-card-header">
                <p>Day {{ selectedWorkout < 10 ? "0" + ((selectedWorkout + 1)) : (selectedWorkout + 1) }}</p>
                        <i class="fa-solid fa-dumbbell"></i>
            </div>
            <h2>{{ workoutType[selectedWorkout % 3] }} Workout </h2>
        </div>
        <div class="workout-grid">
            <h4 class="grid-name">Warmup</h4>
            <h6>Sets</h6>
            <h6>Reps</h6>
            <h6 class="grid-weight">Weight</h6>
            <div class="workout-grid qwerty" v-for="(w, wIdx) in workout" key="wIdx">
                <div class="grid-name">
                    <p>{{ w.name }}</p>
                    <button class="question-btn">
                        <i @click="() => { selectedExercise = w.name }" class="fa-regular fa-circle-question"></i>
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
                <div class="workout-grid qwerty" v-for="(w, wIdx) in workout" key="wIdx">
                    <div class="grid-name">
                        <p>{{ w.name }}</p>
                        <button class="question-btn">
                            <i @click="() => { selectedExercise = w.name }" class="fa-regular fa-circle-question"></i>
                        </button>
                    </div>
                    <p>{{ w.sets }}</p>
                    <p>{{ w.reps }}</p>
                    <input v-model="props.data[props.selectedWorkout][w.name]" type="text" placeholder="14kg"
                        class="grid-weight">
                </div>
            </div>
        </div>
        <div class="card workout-btns">
            <button @click="handleSaveWorkout">Save & Exit <i class="fa-solid fa-save"></i></button>
            <button :disabled="!isWorkoutCompleted" @click="handleCompleteWorkout">Complete <i
                    class="fa-solid fa-check"></i></button>
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

.plan-card-header,
.workout-btns {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 1rem;
}

.workout-grid,
.qwerty {
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
    display: flex;
    align-items: center;
    gap: 1rem;
}

.grid-name button {
    padding: 0;
    border: none;
    box-shadow: none;
}

.grid-name button:hover {
    transform: none;
    box-shadow: none;
    color: var(--color-link);
}

/* hello next copy */
.question-btn {
    opacity: 0;
    pointer-events: none;
}

.qwerty:hover .question-btn {
    opacity: 1;
    pointer-events: all;
}

.grid-name p {
    text-transform: capitalize;
}

.grid-weights {
    grid-column: span 2 / span 2;
}

.workout-btns button {
    flex: 1;
}

.workout-btns button i {
    padding-left: 0.5rem;
}

.exercise-description {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    width: 100%;
}

.exercise-description h3 {
    text-transform: capitalize;
}

.exercise-description button i {
    padding-left: 0.5rem;
}
</style>