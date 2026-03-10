<template>

  <main class="container mx-auto space-x-auto my-4 space-y-4">
    
    <h1 class="text-3xl text-center text-teal-800 font-semibold">Abner's Event Booking Application!</h1>
    
    <h2 class="text-xl text-center text-teal-800 underline">All Available Events</h2>
    
    <section class="grid grid-cols-2 gap-4">
      <template v-if="currentlyLoading == false">
        <EventCardComponent
        v-for="event in eventlist" :key="event.id" 
        :title="event.title"
        :time="event.date"
        :description="event.description"
        @register="registerForEvent(event)"
        />
      </template>
      <!-- v-else -->
      <template v-else>
        <LoadingCardComponent v-for="i in 16" :key="i"/>
      </template>
       <!-- if events are still loading, show the loading card component instead of event cards -->
    </section>

    <h2 class="text-xl text-center text-teal-800 underline">Your Booked Events</h2>

      <section class="grid grid-cols-1 gap-4">
        <template v-if="loadingBookings == false">
          <BookedEventCardComponent
          v-for="booking in bookingList"
          :key="booking.bookingID" 
          :title="booking.eventTitle"
          :status="booking.status"
          @dropout="console.log('Dropout Event Emitted!')"
          />
        </template>
        <!-- v-else -->
        <template v-else>
          <LoadingBookingComponent v-for="i in 4" :key="i"/>
        </template>
       <!-- if events are still loading, show the loading card component instead of event cards -->
      </section>

    <!-- section to display user's booked events, currently empty bc its unimplemented -->
  </main>
</template>

<script setup>
  import { ref, onMounted } from 'vue';
  import LoadingCardComponent from '@/components/LoadingCardComponent.vue';
  import LoadingBookingComponent from '@/components/LoadingBookingComponent.vue';
  import EventCardComponent from '@/components/EventCardComponent.vue';
  import BookedEventCardComponent from './components/BookedEventCardComponent.vue';
  //importing the cards to be used in this parent component

  const eventlist = ref([]);
  const bookingList = ref([]);
  //state to hold list of events
  const currentlyLoading = ref(false);
  const loadingBookings = ref(false);
  //state to hold loading status for events and bookings

  const fetchEvents = async () => {
    try {
      currentlyLoading.value = true;
      const response = await fetch('http://localhost:3420/events');
      eventlist.value = await response.json();
      console.log('Fetched events successfully!');
    } catch (error) {
      console.error('Error fetching events:', error);
    }
    finally {
      currentlyLoading.value = false;
    }
  };

  const fetchBookings = async () => {
    try {
      loadingBookings.value = true;
      const response = await fetch('http://localhost:3420/bookings');
      bookingList.value = await response.json();
      console.log('Fetched bookings successfully!');
    } catch (error) {
      console.error('Error fetching bookings:', error);
    }
    finally {
      loadingBookings.value = false;
    }
  };

  onMounted(() => {
    fetchEvents();
    fetchBookings();
  });
  //fetch events and bookings from backend API on component mount

  const registerForEvent = async (event) => {
    if (bookingList.value.some(booking => booking.eventID === event.id && booking.userID === 2)) {
      alert('You\'re already registered for this event!');
      return;
    }

    console.log(`Registering for event with ID: ${event.id}`);
    // Implement registration logic here, e.g., send POST request to backend
    const eventToBook = {
      bookingID: Date.now(), // Generate a unique ID for the booked event
      userID: 2, // Example user ID, replace with actual user ID from authentication
      eventID: event.id,
      eventTitle: event.title,
      status: 'Booking' //status is in progress, basically
    };
    bookingList.value.push(eventToBook); //update the UI with the new booking

    try {
      const response = await fetch('http://localhost:3420/bookings', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          ...eventToBook, //spread operator copies every element from eventToBook object into the body of the POST request
          status: 'Booked' // Add a status field to indicate the booking status
        })
      });
    
      if (response.ok) {
        const index = bookingList.value.findIndex(booking => booking.bookingID === eventToBook.bookingID);
        bookingList.value[index] = await response.json();
        //update the booking in the UI with the response from the backend, which includes the updated status
      }
      else {
        throw new Error('Event registration failed :()');
      }

    }
    catch (error) {
        console.error('Error registering for event:', error);
        bookingList.value = bookingList.value.filter(booking => booking.bookingID !== eventToBook.bookingID);
        //remove the booking from the UI if the registration fails
    }
    ;

  };

</script>