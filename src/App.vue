<script setup>
    import Card from './components/Card.vue';
    import Menu from './components/Menu.vue';
    
    let images = ['img/paire1.png', 'img/paire2.png', 'img/paire3.png', 'img/paire4.png', 'img/paire5.png', 'img/paire6.png', 'img/paire1.png', 'img/paire2.png', 'img/paire3.png', 'img/paire4.png', 'img/paire5.png', 'img/paire6.png'];

    for (let i = images.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [images[i], images[j]] = [images[j], images[i]];
    }

    let cardNumbers = ['card1', 'card2', 'card3', 'card4', 'card5', 'card6', 'card7', 'card8', 'card9', 'card10', 'card11', 'card12'];
</script>

<template>
    <Menu />
    <div class="container hide" id="CardContainer">
        <Card v-for="(cardNumber, index) in cardNumbers" :key="cardNumber" :Card="'card'" :CardNumber="cardNumber" :image="images[index]" />
    </div>
</template>