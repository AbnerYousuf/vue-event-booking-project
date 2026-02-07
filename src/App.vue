<template>

  <main class="container mx-auto space-x-auto my-4 space-y-4">
    
    <h1 class="text-3xl text-center text-teal-800 font-semibold">Abner's Event Booking Application!</h1>
    
    <h2 class="text-xl text-center text-teal-800 underline">All Available Events</h2>
    
    <section class="grid grid-cols-2 gap-4">

      <EventCardComponent v-for="i in 8" :key="i" 
      title="Internship/Job 2026"
      time="2026-08-01"
      description="Please let this happen!"
      @register="console.log('Register Event Emitted!')"
      @dropout="console.log('Dropout Event Emitted!')"
      />
      <!-- dummy data for 8 event cards -->
    </section>
    
    <h2 class="text-xl text-center text-teal-800 underline">Your Booked Events</h2>
    <!-- section to display user's booked events, currently empty bc its unimplemented -->
  </main>
</template>

<script setup>
  import EventCardComponent from '@/components/EventCardComponent.vue';
  //importing the EventCardComponent to be used in this parent component
</script>