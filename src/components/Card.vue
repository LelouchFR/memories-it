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
            <img src="img/placeholder.png" alt="back of card" draggable="false" />
        </div>
    </div>
</template>

<script>
    let FlipNums = 0, foundPairs = 0;
    let resultPairs = [], correctResultPars = [], CardPair = [], CardPairTurner = [];
    let resultChecker = [
        ['img/Angular.png', 'img/Angular.png'],
        ['img/React.png', 'img/React.png'],
        ['img/Vue.jpg', 'img/Vue.jpg'],
        ['img/NodeJS.jpg', 'img/NodeJS.jpg'],
        ['img/Preact.png', 'img/Preact.png'],
        ['img/Svelte.png', 'img/Svelte.png']
    ];
    let youWon = false;

    function wait(time) {
        return new Promise(resolve => setTimeout(resolve, time));
    }

    function CheckCards(FirstCard, SecondCard, firstTurn, secondTurn) {
        if (FirstCard === SecondCard) {
            foundPairs++;
            resultPairs.push([FirstCard, SecondCard]);
            for (let i = 0; i < resultChecker.length; i++) {
                if (!resultChecker.includes(resultPairs[i]) && resultPairs.length === resultChecker.length) {
                    youWon = true;
                }
            }
        } else {
            firstTurn.isFlipped = !firstTurn.isFlipped;
            secondTurn.isFlipped = !secondTurn.isFlipped;
        }
        CardPair = [], CardPairTurner = [];
    }
    
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
                CardPair.push(this.image);
                CardPairTurner.push(this);
                FlipNums++;
                if (FlipNums === 2) {
                    CheckCards(CardPair[0], CardPair[1], CardPairTurner[0], CardPairTurner[1]);
                    FlipNums = 0;
                }
            },
        },
    };
</script>