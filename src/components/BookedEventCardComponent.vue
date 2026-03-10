<template>

    <SectionedCardComponent>

        <section class="flex justify-between gap-2 p-2">
            <div>
                <h3 class="text-lg font-semibold text-teal-800 p-2">{{ title }}</h3>
                <span class="bg-teal-400 text-white rounded-full px-2 py-2 text-sm">Status: {{ status }}</span>
            </div>

            <!-- display event information passed from parent component via props -->

            <ButtonComponent @clickevent="$emit('dropout')" eventtext="Drop Out" variant="red" />
            <!-- button to trigger deregistration event emitted to parent component -->
        </section>
    </SectionedCardComponent>

</template>

<script setup>
    import SectionedCardComponent from '@/components/SectionedCardComponent.vue';
    import ButtonComponent from '@/components/ButtonComponent.vue';
    defineProps({
        title: String,
        status: String
    });
    //props to handle event information passed from parent component

    defineEmits(['dropout'])
    //events to handle event registration/deregistration
</script>