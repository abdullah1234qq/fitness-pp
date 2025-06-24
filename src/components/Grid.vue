<script setup>
import { workoutProgram } from "../utils/next.js"
const workoutTypes = ["push", "pull", "legs"]
</script>
<template>
    <section id="grid">
        <button v-for="workout in Object.keys(workoutProgram)" class="card-button plan-card">
            <div class="">
                <p>Day 1</p>
                ICON
            </div>
            <h3></h3>
        </button>
    </section>
</template>
<style scoped></style>