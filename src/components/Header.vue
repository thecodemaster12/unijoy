<script setup>
import DarkModeToggle from './DarkModeToggle.vue';

</script>

<template>
    <section class="shadow dark:bg-gray-900 dark-transition dark:border-b dark:border-white">
        <div class="container mx-auto flex justify-between items-center py-6">
            <h2 class="text-2xl text-black dark:text-white">UniJoy</h2>
            <DarkModeToggle />
        </div>
    </section>
</template>

<style scoped>
</style>