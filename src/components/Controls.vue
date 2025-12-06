<script setup>
import { PhArrowBendLeftUp, PhArrowBendRightDown,PhBroom } from '@phosphor-icons/vue';
</script>

<template>
    <div class="w-full flex justify-center flex-wrap py-2 gap-2">
        <!-- <button class="control-btn flex items-center">
            <PhArrowBendLeftUp :size="25" class="mb-4" /> Unicode to Bijoy
        </button>
        <button class="control-btn flex items-center">Bijoy to Unicode
            <PhArrowBendRightDown :size="25" class="mt-4" />
        </button> -->

        <button class="flex items-center gap-2 bg-red-600 px-4 py-2 rounded text-white text-lgl">Clear Text <PhBroom :size="22" /></button>
    </div>
</template>