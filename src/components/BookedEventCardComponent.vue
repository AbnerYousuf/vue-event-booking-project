<template>

    <BaseCardComponent>

        <h3 class="text-lg font-semibold text-teal-800 p-2">{{ title }}</h3>
        <!-- display event information passed from parent component via props -->

        <section class="flex justify-end gap-2 p-2">
            <Button @clickevent="$emit('register')" eventtext="Register" />
            <Button @clickevent="$emit('dropout')" eventtext="Drop Out" variant="red" />
        </section>
        <!-- buttons to trigger registration/deregistration events emitted to parent component -->
    </BaseCardComponent>

</template>

<script setup>
    import BaseCardComponent from '@/components/BaseCardComponent.vue';
    import Button from '@/components/Button.vue';
    //importing the Button component to be used within this EventCardComponent
    defineProps({
        title: String
    });
    //props to handle event information passed from parent component

    defineEmits(['register','dropout'])
    //events to handle event registration/deregistration
</script>