<script setup>
import { ref } from 'vue';
import Greetings from './Greetings.vue';
import Controls from './Controls.vue';
import { ConvertToUnicode, ReArrangeUnicodeConvertedText } from '../bjoytouni';

const unicodeText = ref('');
const bijoyText = ref('');

const bijoytouni = (text) => {
    console.log(text);
    
    unicodeText.value = ConvertToUnicode('bijoy',text);
}

// const convert = (text) => {
    
// }

const message = ref({
    title: 'Unicode to Bijoy Converter',
    description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, eaque. Aliquid est ducimus molestiae laboriosam et blanditiis molestias saepe dignissimos provident commodi. Nam, ea iste reprehenderit officia deleniti ex non?'
})
</script>

<template>
    <section class="dark:bg-gray-900 dark-transition">
        <div class="container mx-auto px-6 h-full flex flex-col gap-6 justify-center items-center">
            <div class="">
                <!-- <Greetings :msg="message" /> -->
                 <p class="text-black dark:text-white">Uni: {{ unicodeText }}</p>
                 <p class="text-black dark:text-white">Bjo: {{ bijoyText }}</p>
            </div>

            <div class="w-full flex flex-col gap-4">
                <textarea name="" id="" placeholder="Unicode Text" class="w-full p-2 border rounded text-black dark:bg-gray-800 dark:text-white dark-transition" rows="8" v-model="unicodeText"></textarea>
                <!-- <Controls /> -->
                            <button class="btn btn-success btn-lg" id="btnToBijoy" type="button">TO BIJOY
                            </button>
                            <button class="btn btn-warning btn-lg" id="btnToUnicode" type="button">
                                TO UNICODE
                            </button>
                            <button class="btn btn-danger btn-lg" id="btnClearAll" type="button">RESET
                            </button>
                <textarea @keyup="bijoytouni(bijoyText)" name="" id="" placeholder="Bijoy Text" class="w-full p-2 border rounded text-black dark:bg-gray-800 dark:text-white dark-transition" rows="8" v-model="bijoyText"></textarea>
            </div>
        </div>
    </section>
</template>