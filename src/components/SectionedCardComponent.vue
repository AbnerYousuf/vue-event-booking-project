<template>
    <BaseCardComponent>
        <h3 v-if="$slots.title" class="text-lg font-semibold text-teal-800 p-2 border-b border-teal-100">
            <slot name="title"></slot>
        </h3>
        <div :class="{'p-2': true, 'border-b text-teal-700 border-teal-100':$slots.description }">
            <slot></slot>
        </div>
        <div v-if="$slots.description" class="text-teal-700 p-2 border-teal-100">
            <slot name="description"></slot>
        </div>
        <div v-if="$slots.buttons" class="text-teal-700 p-2 border-teal-100">
            <slot name="buttons"></slot>
        </div>
    </BaseCardComponent>
</template>

<script setup>
    import BaseCardComponent from '@/components/BaseCardComponent.vue';
</script>