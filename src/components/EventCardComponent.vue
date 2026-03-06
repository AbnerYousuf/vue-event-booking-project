<template>

    <SectionedCardComponent>
        <!-- display event information in named slots passed from parent component via props -->
        <template #title>
            {{ title }}
        </template>
        {{ time }}
        <template #description>
                {{ description }}
        </template>
        <template #buttons>
            <div class="flex justify-end gap-2">
                <Button @clickevent="$emit('register')" eventtext="Register" />
            </div>
            <!-- buttons to trigger registration/deregistration events emitted to parent component -->
        </template>
    </SectionedCardComponent>
</template>

<script setup>
    import SectionedCardComponent from '@/components/SectionedCardComponent.vue';
    import BaseCardComponent from '@/components/BaseCardComponent.vue';
    import Button from '@/components/Button.vue';
    //importing the Button component to be used within this EventCardComponent
    defineProps({
        title: String,
        time: String,
        description: String
    });
    //props to handle event information passed from parent component

    defineEmits(['register','dropout'])
    //events to handle event registration/deregistration
</script>