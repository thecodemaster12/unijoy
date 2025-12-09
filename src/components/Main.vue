<script setup>
import { ref } from 'vue';
import Greetings from './Greetings.vue'
import Controls from './Controls.vue'
import { ConvertToUnicode, ConvertToASCII } from '../converter';
import { PhClipboardText } from '@phosphor-icons/vue';

const message = ref({
  title: 'Your Bangla Text Conversion Companion',
  description: 'Convert Bangla text between Unicode and Bijoy formats.'
})

const bijoyText = ref('');
const unicodeText = ref('');
const copiedUnicode = ref(false)
const copiedBijoy = ref(false)

let timer

const unicodeToBijoy = () => {
  clearTimeout(timer)
  timer = setTimeout(() => {
    bijoyText.value = ConvertToASCII(unicodeText.value)
  }, 300)
}

const bijoyToUnicode = () => {
  clearTimeout(timer)
  timer = setTimeout(() => {
    unicodeText.value = ConvertToUnicode(bijoyText.value)
  }, 300)
}

const copyUni = () => {
  navigator.clipboard.writeText(unicodeText.value)
  copiedUnicode.value = true
  setTimeout(() => copiedUnicode.value = false, 1000)
}
const copyBijoy = () => {
  navigator.clipboard.writeText(bijoyText.value)
  copiedBijoy.value = true
  setTimeout(() => copiedBijoy.value = false, 1000)
}

const clearText = () => {
  const uni = document.querySelector('#unicodeText');
  const bijoy = document.querySelector('#bijoyText');


  uni.classList.add('text-fade-out');
  bijoy.classList.add('text-fade-out');

  setTimeout(() => {
    unicodeText.value = '';
    bijoyText.value = '';
    uni.classList.remove('text-fade-out');
    bijoy.classList.remove('text-fade-out');
  }, 300);
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
            class="w-full h-52 p-4 text-lg border border-gray-900 dark:border-gray-200 rounded text-black bg-white dark:bg-gray-800 dark:text-white dark-transition"
            v-model="unicodeText" @input="unicodeToBijoy()" placeholder="ইউনিকোড কি-বোর্ডের লেখা এখানে পেস্ট করুন...">
            </textarea>
          <PhClipboardText @click="copyUni" class="absolute top-1 text-black dark:text-gray-300 right-1 cursor-pointer"
            :class="{ 'text-indigo-500': copiedUnicode }" :size="26" />
        </div>

        <Controls @bijoyToUnicode="bijoyToUnicode" @unicodeToBijoy="unicodeToBijoy" @clearText="clearText" />

        <div class="relative">
          <textarea id="bijoyText"
            class="w-full h-52 p-4 text-xl border border-gray-900 dark:border-gray-200 rounded text-black dark:bg-gray-800 dark:text-white dark-transition font-smj"
            v-model="bijoyText" @input="bijoyToUnicode()"
            placeholder="বিজয় কি-বোর্ডের লেখা এখানে পেস্ট করুন..."></textarea>

          <PhClipboardText @click="copyBijoy"
            class="absolute top-1 text-black dark:text-gray-300 right-1 cursor-pointer"
            :class="{ 'text-indigo-500': copiedBijoy }" :size="26" />
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