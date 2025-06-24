<script setup>
import { gymHealthFacts } from "../../utils/next.js"

const randomNumber = Math.floor(Math.random() * gymHealthFacts.length)
</script>
<template>
    <section id="dashboard">
        <div class="card tip-container">
            <h2> Welcome to dashboard</h2>
            <div>
                <p class="tip"><strong>Daily Tip</strong><br />INJECT THE TIP</p>
            </div>
        </div>
    </section>

</template>
<style scoped></style>