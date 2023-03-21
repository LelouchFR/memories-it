<script setup>
    import Card from './components/Card.vue';
</script>

<template>
    <div class="container">
        <Card Card="card" CardNumber="card1" image="img/Angular.png" title="Angular"/>
        <Card Card="card" CardNumber="card2" image="img/NodeJs.jpg" title="Node Js"/>
        <Card Card="card" CardNumber="card3" image="img/Preact.png" title="Preact"/>
        <Card Card="card" CardNumber="card4" image="img/React.png" title="React"/>
        <Card Card="card" CardNumber="card5" image="img/Svelte.png" title="Svelte"/>
        <Card Card="card" CardNumber="card6" image="img/Vue.jpg" title="Vue"/>
    </div>
</template>