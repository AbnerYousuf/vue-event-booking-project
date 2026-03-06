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
                <ButtonComponent @clickevent="$emit('register')" eventtext="Register" />
            </div>
            <!-- buttons to trigger registration/deregistration events emitted to parent component -->
        </template>
    </SectionedCardComponent>
</template>

<script setup>
    import SectionedCardComponent from '@/components/SectionedCardComponent.vue';
    import ButtonComponent from '@/components/ButtonComponent.vue';
    defineProps({
        title: String,
        time: String,
        description: String
    });
    //props to handle event information passed from parent component

    defineEmits(['register','dropout'])
    //events to handle event registration/deregistration
</script>