<template>

    <div class="bg-teal-50 border-teal-950 rounded-lg p-2">

        <h3 class="text-lg font-semibold text-teal-800 p-2 border-b border-teal-100">{{ title }}</h3>
        <p class="text-teal-700 p-2 border-b border-teal-100">{{ time }}</p>
        <p class="text-teal-700 p-2 border-b border-teal-100">{{ description }}</p>
        <!-- display event information passed from parent component via props -->

        <section class="flex justify-end gap-2 p-2">
            <button @click="$emit('register')" class="bg-teal-200 text-white px-4 py-2 rounded hover:bg-teal-400">
                Register
            </button>
            <button @click="$emit('dropout')" class="bg-red-200 text-white px-4 py-2 rounded hover:bg-red-400">
                Drop Out
            </button>
        </section>
        <!-- buttons to trigger registration/deregistration events emitted to parent component -->
    </div>

</template>

<script setup>
    defineProps({
        title: String,
        time: String,
        description: String
    });
    //props to handle event information passed from parent component

    defineEmits(['register','dropout'])
    //events to handle event registration/deregistration
</script>