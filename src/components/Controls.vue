<script setup>
import { PhArrowBendLeftUp, PhArrowBendRightDown   } from '@phosphor-icons/vue';
</script>

<template>
    <div class="w-full flex justify-center flex-wrap py-2 gap-2">
        <button class="control-btn flex items-center">
            <PhArrowBendLeftUp :size="25" class="mb-4" /> Unicode to Bijoy
        </button>
        <button class="control-btn flex items-center">Bijoy to Unicode
            <PhArrowBendRightDown :size="25" class="mt-4" />
        </button>
    </div>
</template>