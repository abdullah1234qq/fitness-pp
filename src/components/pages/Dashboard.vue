<script setup>
import { gymHealthFacts } from "../../utils/next.js"
import Grid from "../../components/Grid.vue"

const props = defineProps({
    handleSelectWorkout: Function,
    firstIncompleteWorkoutIndex: Number,
})

const randomNumber = Math.floor(Math.random() * gymHealthFacts.length)
const todaysFact = gymHealthFacts[randomNumber]

</script>
<template>
    <section id="dashboard">
        <div class="card tip-container">
            <h2> Welcome to dashboard</h2>
            <div>
                <p class="tip"><strong>Daily Tip</strong><br />{{ todaysFact }}</p>
            </div>
            <button
                @click="handleSelectWorkout(firstIncompleteWorkoutIndex < 0 ? 0 : firstIncompleteWorkoutIndex)">Start
                workout &rarr;</button>
        </div>
        <br />
        <Grid v-bind="props" />
    </section>

</template>
<style scoped>
.tip-container,
.tip-container div,
#dashboard {
    display: flex;
}

.tip-container,
#dashboard {
    flex-direction: column;
}
</style>