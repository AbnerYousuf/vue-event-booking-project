<template>
    <button @click="$emit('clickevent')" class="bg-teal-200 text-white px-4 py-2 rounded hover:bg-teal-400">
                {{ eventtext }}
            </button>
</template>

<script setup>
    defineProps({
        eventtext: String
        //text to display on button, passed from parent component via props
    });
</script>