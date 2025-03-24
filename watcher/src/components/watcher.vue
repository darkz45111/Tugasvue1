<script setup>
import { ref, watch } from 'vue';

const counter = ref(0);
const message = ref('');
const isMultipleOfFive = ref(false);

watch(counter, (newValue, oldValue) => {
  if (newValue !== 0 && newValue % 5 === 0) {
    message.value = `Counter mencapai ${newValue}, kelipatan 5!`;
    isMultipleOfFive.value = true;
  } else {
    message.value = `Counter berubah dari ${oldValue} ke ${newValue}`;
    isMultipleOfFive.value = false;
  }
});

const increment = () => {
  counter.value++;
};

const decrement = () => {
  if (counter.value > 0) {
    counter.value--;
  }
};
</script>

<template>
  <div class="container">
    <h2>Watcher Counter</h2>
    <p :class="{ 'multiple-of-five': isMultipleOfFive }"> Nilai counter: {{ counter }} </p>
    <button @click="decrement">Kurangi</button>
    <button @click="increment">Tambah</button>
    <p v-if="message" :class="{ 'green-text': isMultipleOfFive }">{{ message }}</p>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
  font-family: Arial, sans-serif;
  margin-top: 50px;
}

button {
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  margin: 5px;
}

p {
  color: rgb(237, 237, 237);
}

p.multiple-of-five {
  color: green;
  font-weight: bold;
}

p.green-text {
  color: green;
  font-weight: bold;
}
</style>
