<script setup></script>
<template>
    <header>
        <h1 class="text-gradient"> Hi 👋 I am Abdullah Hussain </h1>
    </header>
    <main>
        <slot />
    </main>
    <footer>
        <small>Created by </small>
        <a href="https://www.github.com/abdullah1234qq" target="_blank">Abdullah Hussain </a>
    </footer>
</template>
<style scoped>
header,
footer,
main {
    padding: 1rem;
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
}

a {
    text-decoration: none;
}

main {
    padding: 1;
}

footer {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    align-items: center;
    padding: 3rem 0;
}
</style>