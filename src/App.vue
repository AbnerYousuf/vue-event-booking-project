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

      <section class="grid grid-cols-1 gap-4">

      <BookedEventCardComponent v-for="i in 8" :key="i" 
      title="Internship/Job 2026"
      @dropout="console.log('Dropout Event Emitted!')"
      />
      <!-- dummy data for 8 event cards -->
    </section>
    <!-- section to display user's booked events, currently empty bc its unimplemented -->
  </main>
</template>

<script setup>
  import { ref, onMounted } from 'vue';

  import EventCardComponent from '@/components/EventCardComponent.vue';
  import BookedEventCardComponent from './components/BookedEventCardComponent.vue';
  //importing the cards to be used in this parent component

  const eventlist = ref([]);
  //state to hold list of events
  const fetchEvents = async () => {
    try {
      const response = await fetch('http://localhost:3420/events');
      eventlist.value = await response.json();
      console.log('Fetched events:', eventlist.value);
    } catch (error) {
      console.error('Error fetching events:', error);
    }
  };

  onMounted(() => {
    fetchEvents();
  });
  //fetch events from backend API on component mount

</script>