<script setup>
import {
    PhArrowBendLeftUp,
    PhArrowBendRightDown,
    PhBroom,
} from "@phosphor-icons/vue";

const emit = defineEmits(["bijoyToUnicode", "unicodeToBijoy", "clearText"]);

const bijoyToUnicode = () => {
    emit("bijoyToUnicode");
};
const unicodeToBijoy = () => {
    emit("unicodeToBijoy");
};
const clearText = () => {
    emit("clearText");
};
</script>

<template>
    <div class="w-full flex justify-center flex-wrap py-2 gap-2">
        <button @click="bijoyToUnicode" class="control-btn flex items-center">
            <PhArrowBendLeftUp :size="25" class="mb-4" /> Bijoy to Unicode
        </button>
        <button @click="unicodeToBijoy" class="control-btn flex items-center">
            Unicode to Bijoy
            <PhArrowBendRightDown :size="25" class="mt-4" />
        </button>
        <button @click="clearText()"
            class="flex items-center gap-2 bg-red-600 hover:bg-red-500 cursor-pointer px-4 py-2 rounded text-white text-lgl">
            Clear Text
            <PhBroom :size="22" />
        </button>
    </div>
</template>
