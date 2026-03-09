<template>
    <BaseCardComponent class="animate-pulse">
        <div class="text-lg font-semibold text-teal-800 p-2 border-b border-teal-100">Retrieving events...</div>
        <div class="text-teal-800 p-2 border-b border-teal-100">Please wait...</div>
        <div class="text-teal-800 p-2">This may take a few seconds...</div>
        <div class="flex justify-end gap-2">
            <ButtonComponent eventtext="Disabled" :disabled="true" hover:bg-teal-200 />
        </div>
    </BaseCardComponent>
</template>

<script setup>
  import BaseCardComponent from '@/components/BaseCardComponent.vue';
  import ButtonComponent from './ButtonComponent.vue';
  //importing the base card component for styling consistency
</script>