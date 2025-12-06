<script setup>
  import { ref } from 'vue';
  import Greetings from './Greetings.vue'
  import Controls from './Controls.vue'
  import { ConvertToUnicode, ConvertToASCII } from '../converter';
  import { PhClipboardText, PhBroom } from '@phosphor-icons/vue';

  const message = ref({
    title: 'Your Bangla Text Conversion Companion',
    description: 'Convert Bangla text between Unicode and Bijoy formats.'
  })

  const bijoyText = ref('');
  const unicodeText = ref('');
  const copied = ref(false);

  const bijoyToUnicode = () => {
    unicodeText.value = ConvertToUnicode(bijoyText.value);
  };

  const unicodeToBijoy = () => {
    bijoyText.value = ConvertToASCII(unicodeText.value);
  };

  const handleClear = () => {

    // bijoyText.value = '';
    // unicodeText.value = '';
  };

  const copyUni = () => {
    navigator.clipboard.writeText(unicodeText.value);
    copied.value = true;
    setTimeout(() => {
      copied.value = false;
    }, 1000);
  }

  const copyBijoy = () => {
    navigator.clipboard.writeText(bijoyText.value);
    copied.value = true;
    setTimeout(() => {
      copied.value = false;
    }, 1000);
  }

  const clearText = () => {
  const uni = document.querySelector('#unicodeText');
  const bijoy = document.querySelector('#bijoyText');

  // Fade both textareas
  uni.classList.add('text-fade-out');
  bijoy.classList.add('text-fade-out');

  // After fade animation, clear AND remove fade class
  setTimeout(() => {
    unicodeText.value = '';
    bijoyText.value = '';
    uni.classList.remove('text-fade-out');
    bijoy.classList.remove('text-fade-out');
  }, 500);
  }
</script>

<template>
  <section class="dark:bg-gray-900 dark-transition">
    <div class="container mx-auto px-6 h-full flex flex-col gap-6 justify-center items-center">
      <div class="">
        <Greetings :msg="message" />
      </div>

      <div class="w-full flex flex-col gap-4">
        <div class="relative">
          <textarea id="unicodeText"
            class="w-full p-4 text-lg border border-gray-900 dark:border-gray-200 rounded text-black bg-white dark:bg-gray-800 dark:text-white dark-transition"
            rows="8" v-model="unicodeText" @input="unicodeToBijoy"
            placeholder="ইউনিকোড কি-বোর্ডের লেখা এখানে পেস্ট করুন...">
            </textarea>
          <PhClipboardText @click="copyUni" class="absolute top-1 text-black dark:text-gray-300 right-1 cursor-pointer"
            :class="{ 'text-indigo-500': copied }" :size="26" />
        </div>

        <!-- <Controls /> -->

        <div class="w-full flex justify-center flex-wrap py-2 gap-2">
          <button @click="clearText" class="flex items-center gap-2 bg-red-600 hover:bg-red-500 cursor-pointer px-4 py-2 rounded text-white text-lgl">Clear Text <PhBroom :size="22" /></button>
        </div>

        <div class="relative">
          <textarea id="bijoyText"
            class="w-full p-4 text-xl border border-gray-900 dark:border-gray-200 rounded text-black dark:bg-gray-800 dark:text-white dark-transition font-smj"
            rows="8" v-model="bijoyText" @input="bijoyToUnicode"
            placeholder="বিজয় কি-বোর্ডের লেখা এখানে পেস্ট করুন..."></textarea>

          <PhClipboardText @click="copyBijoy" class="absolute top-1 text-black dark:text-gray-300 right-1 cursor-pointer"
            :class="{ 'text-indigo-500': copied }" :size="26" />
        </div>
      </div>
    </div>
  </section>
</template>


<style scoped>
  .text-fade-out {
    color: transparent;
  }
</style>