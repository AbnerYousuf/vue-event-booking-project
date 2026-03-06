<template>
    <button @click="$emit('clickevent')" :class="buttonClasses">
                {{ eventtext }}
            </button>
</template>

<script setup>
    import { computed } from 'vue';
    defineEmits(['clickevent']);
    const props = defineProps({
        eventtext: String,
        variant: {
            type: String,
            default: 'teal'
        }
        //text to display on button, passed from parent component via props
    });

    const buttonClasses = computed(() => {
        const baseClasses = 'text-white px-4 py-2 rounded';
        if (props.variant === 'red') {
            return `${baseClasses} bg-red-200 enabled:hover:bg-red-400`;
        } else {
            return `${baseClasses} bg-teal-200 hover:bg-teal-400`;
        }
    });
</script>