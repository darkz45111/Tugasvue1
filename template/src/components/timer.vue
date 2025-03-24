<script setup>
import { ref, onMounted, onBeforeMount, onUpdated } from 'vue';

const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);
const timer = ref(null);

const startTimer = () => {
    console.log("Tombol start ditekan!");
    if (!timer.value) {
        console.log("Memulai timer...");
        timer.value = setInterval(() => {
            seconds.value++;
            console.log(`Waktu sekarang: ${seconds.value} detik`);

            if (seconds.value === 60) {
                seconds.value = 0;
                minutes.value++;
            }
            if (minutes.value === 60) {
                minutes.value = 0;
                hours.value++;
            }
        }, 1000);
    } else {
        console.log("Timer sudah berjalan.");
    }
};

const pauseTimer = () => {
    console.log("Timer dihentikan.");
    clearInterval(timer.value);
    timer.value = null;
};

const resetTimer = () => {
    console.log("Timer direset.");
    pauseTimer();
    hours.value = 0;
    minutes.value = 0;
    seconds.value = 0;
};

const formatTime = (value) => (value < 10 ? `0${value}` : value);

onBeforeMount(() => {
    console.log('Komponen akan segera dimuat, persiapan dilakukan!');
});

onMounted(() => {
    console.log('Komponen telah dimuat!');
    console.log(`hours: ${hours.value}, minutes: ${minutes.value}, seconds: ${seconds.value}`);
});

onUpdated(() => {
    console.log(`Waktu diperbarui: ${formatTime(hours.value)} : ${formatTime(minutes.value)} : ${formatTime(seconds.value)}`);
});
</script>

<template>
    <div class="container">
        <h2>Timer</h2>
        <p class="timer-display">
            {{ formatTime(hours) }}:{{ formatTime(minutes) }}:{{ formatTime(seconds) }}
        </p>
        <button @click="startTimer">Start</button>
        <button @click="pauseTimer">Pause</button>
        <button @click="resetTimer">Reset</button>
    </div>
</template>

<style scoped>
.container {
    text-align: center;
    font-family: Arial, sans-serif;
    margin-top: 50px;
}

.timer-display {
    font-size: 32px;
    font-weight: bold;
    margin: 10px 0;
}

button {
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
    margin: 5px;
    border: none;
    border-radius: 5px;
    background-color: rgb(96, 201, 40);
    color: antiquewhite;
    transition: background 0.4s;
}

button:hover {
    background-color: blue;
}
</style>
