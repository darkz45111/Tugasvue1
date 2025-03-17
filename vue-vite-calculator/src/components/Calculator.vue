<template>
    <div class="calculator">
      <h2>Kalkulator Vue 🧮</h2>
      <input type="text" v-model="currentValue" disabled />
  
      <div class="buttons">
        <button @click="clearInput">C</button>
        <button @click="appendValue('/')">÷</button>
        <button @click="appendValue('*')">×</button>
        <button @click="appendValue('-')">−</button>
        
        <button v-for="num in numbers" :key="num" @click="appendValue(num)">
          {{ num }}
        </button>
        
        <button @click="appendValue('+')">+</button>
        <button @click="appendValue('.')">.</button>
        <button @click="calculateResult">=</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const currentValue = ref("");
  
  const numbers = [7, 8, 9, 4, 5, 6, 1, 2, 3, 0];
  
  const appendValue = (val) => {
    currentValue.value += val;
  };
  
  const clearInput = () => {
    currentValue.value = "";
  };
  
  const calculateResult = () => {
    try {
      currentValue.value = eval(currentValue.value);
    } catch {
      currentValue.value = "Error!";
    }
  };
  </script>