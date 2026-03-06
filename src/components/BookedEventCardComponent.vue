<template>

    <SectionedCardComponent>

        <h3 class="text-lg font-semibold text-teal-800 p-2">{{ title }}</h3>
        <!-- display event information passed from parent component via props -->

        <section class="flex justify-between gap-2 p-2">
            <ButtonComponent @clickevent="$emit('dropout')" eventtext="Drop Out" variant="red" />
        </section>
        <!-- buttons to trigger registration/deregistration events emitted to parent component -->
    </SectionedCardComponent>

</template>

<script setup>
    import SectionedCardComponent from '@/components/SectionedCardComponent.vue';
    import ButtonComponent from '@/components/ButtonComponent.vue';
    defineProps({
        title: String
    });
    //props to handle event information passed from parent component

    defineEmits(['register','dropout'])
    //events to handle event registration/deregistration
</script>