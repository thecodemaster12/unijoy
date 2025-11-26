<script setup>
import DarkModeToggle from './DarkModeToggle.vue';

</script>

<template>
    <section class="shadow">
        <div class="container mx-auto flex justify-between py-6">
            <h2 class="text-2xl text-black dark:text-white">Header</h2>
            <DarkModeToggle />
        </div>
    </section>
</template>

<style scoped>
</style>