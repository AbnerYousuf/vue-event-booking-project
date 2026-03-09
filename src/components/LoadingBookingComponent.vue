<template>
    <BaseCardComponent class="animate-pulse flex justify-between gap-2 p-2">
        <h3 class="flex-space-8 text-lg font-semibold text-teal-800 p-2 border-teal-100">Retrieving bookings...</h3>
        <!-- display event information passed from parent component via props -->

        <ButtonComponent eventtext="Disabled" :disabled="true" variant="red"/>
        <!-- button to trigger deregistration event emitted to parent component -->
    </BaseCardComponent>
</template>

<script setup>
  import BaseCardComponent from '@/components/BaseCardComponent.vue';
  import ButtonComponent from '@/components/ButtonComponent.vue';
  //importing the base card component for styling consistency
</script>