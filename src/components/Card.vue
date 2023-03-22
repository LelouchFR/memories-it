<script setup>
    const props = defineProps({
        Card: String,
        CardNumber: String,
        image: String,
    });
</script>

<template>
    <div :class="[Card, CardNumber, { 'flipped': isFlipped }]" @click="flipCard">
        <div class="front">
            <img :src="image" alt="image from a JavaScript Framework" draggable="false" />
        </div>
        <div class="back">
            <img src="img/logo.png" alt="back of card" draggable="false" />
        </div>
    </div>
</template>

<script>
    export default {
        name: "Card",
        data() {
            return {
                isFlipped: true,
            };
        },
        methods: {
            flipCard() {
                this.isFlipped = !this.isFlipped;
            },
        },
    };
</script>