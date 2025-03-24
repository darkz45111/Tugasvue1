<script setup>
import { ref } from 'vue';

// Daftar item
const items = ref(['semangka', 'persik', 'jeruk']);

// Input untuk item baru
const newItem = ref('');

// Fungsi menambah item baru ke daftar
const addItem = () => {
  if (newItem.value.trim()) { // Perbaikan kondisi
    items.value.push(newItem.value.trim()); // Tambahkan item ke daftar
    newItem.value = ''; // Reset input
  }
};
</script>

<template>
  <div class="container">
    <h2> Daftar Buah</h2>
    
    <!-- List -->
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    
    <!-- Input dan Tombol -->
    <div class="input-container">
      <input v-model="newItem" placeholder="Tambahkan buah..." />
      <button @click="addItem">Tambah</button>
    </div>
  </div>
</template>

<style scoped>
/* Styling Kontainer */
.container {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  text-align: center;
  background: #ffffff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Judul */
h2 {
  color: #333;
}

/* List Styling */
ul {
  list-style: none;
  padding: 0;
  margin-top: 10px;
}

li {
  background: #f8f9fa;
  padding: 10px;
  margin: 6px 0;
  border-radius: 8px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

/* Input dan Tombol */
.input-container {
  display: flex;
  gap: 10px;
  justify-content: center;
  margin-top: 10px;
}

input {
  flex: 1;
  padding: 10px;
  border: 2px solid #4caf50;
  border-radius: 5px;
  outline: none;
}

button {
  padding: 10px 15px;
  background: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background: #388e3c;
}
</style>
