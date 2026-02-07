<template>
    <div class="bg-teal-50 border-teal-950 rounded-lg p-2">
        <h3 class="text-lg font-semibold text-teal-800 p-2 border-b border-teal-100">{{ title }}</h3>
        <p class="text-teal-700 p-2 border-b border-teal-100">{{ time }}</p>
        <p class="text-teal-700 p-2">{{ description }}</p>
    </div>
</template>

<script setup>
    defineProps({
        title: String,
        time: String,
        description: String
    });
</script>