<script setup>
    import Card from './components/Card.vue';
    
    let images = ['img/Angular.png', 'img/React.png', 'img/Vue.jpg', 'img/Angular.png', 'img/React.png', 'img/Vue.jpg'];

    for (let i = images.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [images[i], images[j]] = [images[j], images[i]];
    }

    let cardNumbers = ['card1', 'card2', 'card3', 'card4', 'card5', 'card6'];
</script>

<template>
    <div class="container">
        <Card v-for="(cardNumber, index) in cardNumbers" :key="cardNumber" :Card="'card'" :CardNumber="cardNumber" :image="images[index]" />
    </div>
</template>