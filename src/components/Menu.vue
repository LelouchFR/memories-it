<template>
    <section class="GameStarter">
        <h1>Memory it !</h1>
        <button @click="Hide_or_Show">Start Playing</button>
        <p><a :href="ghLink">&copy; Baptiste Zahnow {{ new Date().getFullYear() }}</a></p>
    </section>
</template>

<script setup>
    const ghLink = "https://github.com/LelouchFR/memory-it";
    let counter = 0;

    function Hide_or_Show() {
        counter++;
        if (counter % 2 === 0) {
            document.getElementById('CardContainer').classList.add('hide');
            document.getElementById('MenuContainer').classList.remove('hide');
        } else {
            document.getElementById('CardContainer').classList.remove('hide');
            document.getElementById('MenuContainer').classList.add('hide');
        }
    }
</script>