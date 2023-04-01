<template>
    <section class="GameStarter" id="MenuContainer">
        <h1>Memories it !</h1>
        <button @click="Hide_or_Show">Start Playing</button>
        <p><input type="checkbox" name="timer" id="Timer" @click="speedrun = !speedrun"> speedrun mode</p>
        <p><a :href="ghLink">&copy; Baptiste & Anna Zahnow {{ new Date().getFullYear() }}</a></p>
    </section>
    <p class="timer"><span id="seconds">00</span>:<span id="tens">00</span></p>
</template>

<script setup>
    const ghLink = "https://github.com/LelouchFR/memory-it";
    let counter = 0;
    let seconds = 0; 
    let tens = 0; 
    let speedrun = false;
    let Interval;

    function Hide_or_Show() {
        counter++;
        if (counter % 2 === 0) {
            document.getElementById('CardContainer').classList.add('hide');
            document.getElementById('MenuContainer').classList.remove('hide');
        } else {
            document.getElementById('CardContainer').classList.remove('hide');
            document.getElementById('MenuContainer').classList.add('hide');
        }

        if (speedrun) speedMod();
    }

    function speedMod() {    
        clearInterval(Interval);
        Interval = setInterval(startTimer, 10);
    }

    function startTimer () {
        let appendTens = document.getElementById("tens");
        let appendSeconds = document.getElementById("seconds");

        tens++; 
        
        if(tens <= 9) appendTens.innerHTML = "0" + tens;
        
        if (tens > 9) appendTens.innerHTML = tens;
        
        if (tens > 99) {
            seconds++;
            appendSeconds.innerHTML = "0" + seconds;
            tens = 0;
            appendTens.innerHTML = "0" + 0;
        }
            
        if (seconds > 9) appendSeconds.innerHTML = seconds;
    }
</script>