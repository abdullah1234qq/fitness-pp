<script setup></script>
<template>
    <section id="welcome">
        <div class="benefits">
            <h2>Complete this Program <br /> if you want...</h2>
            <div>
                <p>✅ Follow a simple program with proven results.</p>
                <p>💪 Get fit, healthy, strong and absolutely shredded.</p>
                <p>🏋 learn more about gym, training and technique</p>

            </div>
        </div>
        <div>
            <h3>Training Plan</h3>
            <p>This training plan follows a structure known as the <strong>Bro split</strong>.</p>
            <h5><i> push &rarr; pull &rarr; Legs &rarr; Repeat</i></h5>
        </div>
        <div class="card cchallenge">
            <h3>🔥 Your Challenge</h3>
            <p>Complete all the workouts and track your progress along all way!</p>
            <p>Do you accept?</p>
            <button>Begin &rarr;</button>
        </div>
    </section>
</template>
<style scoped>
#welcome,
.challenge,
.benefits {
    display: flex;
    flex-direction: column;
}

#welcome {
    gap: 1.2rem;
}

.benefits {
    gap: 0.5rem;
}

.challenge {
    gap: 0.25rem;
}
</style>