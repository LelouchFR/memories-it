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
            <img src="/img/back.png" alt="back of card" draggable="false" />
        </div>
    </div>
</template>

<script>
    let FlipNums = 0, foundPairs = 0;
    let resultPairs = [], correctResultPairs = [], CardPair = [], CardPairTurner = [];
    let resultChecker = [
        ['img/paire1.png', 'img/paire1.png'],
        ['img/paire2.png', 'img/paire2.png'],
        ['img/paire3.png', 'img/paire3.png'],
        ['img/paire4.png', 'img/paire4.png'],
        ['img/paire5.png', 'img/paire5.png'],
        ['img/paire6.png', 'img/paire6.png']
    ];

    let youWon = false;

    function CheckCards(FirstCard, SecondCard, firstTurn, secondTurn) {
        if (FirstCard === SecondCard) {
            foundPairs++;
            resultPairs.push([FirstCard, SecondCard]);
            for (let i = 0; i < resultChecker.length; i++)
                if (!resultChecker.includes(resultPairs[i]) && resultPairs.length === resultChecker.length)
                    youWon = true;
        } else {
            setTimeout(() => {
                secondTurn.isFlipped = !secondTurn.isFlipped;
                firstTurn.isFlipped = !firstTurn.isFlipped;
            }, 750);
        }

        if(youWon) console.log("You Won");
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