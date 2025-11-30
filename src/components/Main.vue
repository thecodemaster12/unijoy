<script setup>
import { ref } from 'vue';
import Greetings from './Greetings.vue';

const message = ref({
    title: 'Unicode to Bijoy Converter',
    description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, eaque. Aliquid est ducimus molestiae laboriosam et blanditiis molestias saepe dignissimos provident commodi. Nam, ea iste reprehenderit officia deleniti ex non?'
})
</script>

<template>
    <section class="dark:bg-gray-900 dark-transition">
        <div class="container mx-auto h-full flex flex-col justify-center items-center">
            <Greetings :msg="message" />
            <textarea name="" id="" placeholder="Unicode"></textarea>
            <div class="border w-full flex justify-center flex-wrap py-2 gap-2">
                <button class="control-btn">Unicode to Bijoy</button>
                <button class="control-btn">Bijoy to Unicode</button>
            </div>
        </div>
    </section>
</template>