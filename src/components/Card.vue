<template>
    <div :class="Card, CardNumber">
        <img :src="image" :alt="title">
        <h3>{{ title }}</h3>
    </div>
</template>

<script setup>
    import { defineProps } from 'vue';

    const props = defineProps({
        Card: String,
        CardNumber: String,
        image: String,
        title: String,
    });
</script>

<script>
export default {
  name: 'Card',
};
</script>