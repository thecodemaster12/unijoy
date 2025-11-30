<script setup>
const props = defineProps(
    {
        msg: Object
    }
)
</script>

<template>
    <h1 class="text-4xl text-center text-black dark:text-white">{{ msg.title }}</h1>
    <p class="text-black dark:text-white">{{ msg.description }}</p>
</template>