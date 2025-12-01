<!-- <template>
  <div class="converter-container">
    <h2>Bangla Unicode-Bijoy Converter</h2>
    <div class="text-areas">
      <div class="textarea-group">
        <label for="bijoyText">Bijoy Text</label>
        <textarea id="bijoyText" v-model="bijoyText" @input="bijoyToUnicode" placeholder="Type Bijoy text here..."></textarea>
      </div>
      <div class="textarea-group">
        <label for="unicodeText">Unicode Text</label>
        <textarea id="unicodeText" v-model="unicodeText" @input="unicodeToBijoy" placeholder="Type Unicode text here..."></textarea>
      </div>
    </div>
    <div class="buttons">
      <button @click="handleClear">Clear All</button>
    </div>
  </div>
</template> -->

<template>
    <section class="dark:bg-gray-900 dark-transition">
        <div class="container mx-auto px-6 h-full flex flex-col gap-6 justify-center items-center">
            <div class="">
                <!-- <Greetings :msg="message" /> -->
                 <p class="text-black dark:text-white">Uni: {{ unicodeText }}</p>
                 <p class="text-black dark:text-white">Bjo: {{ bijoyText }}</p>
            </div>

            <div class="w-full flex flex-col gap-4">
                <!-- <textarea name="" id="" placeholder="Unicode Text" class="w-full p-2 border rounded text-black dark:bg-gray-800 dark:text-white dark-transition" rows="8" v-model="unicodeText"></textarea> -->
                <textarea id="unicodeText" 
                class="w-full p-2 border rounded text-black dark:bg-gray-800 dark:text-white dark-transition" 
                rows="8" 
                v-model="unicodeText" 
                @input="unicodeToBijoy" 
                placeholder="Type Unicode text here..."></textarea>
                <!-- <Controls /> -->
                            <button class="btn btn-success btn-lg" id="btnToBijoy" type="button">TO BIJOY
                            </button>
                            <button class="btn btn-warning btn-lg" id="btnToUnicode" type="button">
                                TO UNICODE
                            </button>
                            <button class="btn btn-danger btn-lg" id="btnClearAll" type="button">RESET
                            </button>
                <!-- <textarea @input="" name="" id="" placeholder="Bijoy Text" class="w-full p-2 border rounded text-black dark:bg-gray-800 dark:text-white dark-transition" rows="8" v-model="bijoyText"></textarea> -->
                <textarea id="bijoyText" 
                class="w-full p-2 border rounded text-black dark:bg-gray-800 dark:text-white dark-transition font-smj" 
                rows="8" 
                v-model="bijoyText" 
                @input="bijoyToUnicode" 
                placeholder="Type Bijoy text here..."></textarea>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import { ConvertToUnicode, ConvertToASCII } from '../md';

const bijoyText = ref('');
const unicodeText = ref('');

const bijoyToUnicode = () => {
  unicodeText.value = ConvertToUnicode(bijoyText.value);
};

const unicodeToBijoy = () => {
  bijoyText.value = ConvertToASCII(unicodeText.value);
};

const handleClear = () => {
  bijoyText.value = '';
  unicodeText.value = '';
};
</script>