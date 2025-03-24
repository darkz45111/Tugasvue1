<template>
  <div class="container">

    <listrendering />
  </div>
</template>

<script>
import listrendering from "./components/listrendering.vue";

export default {
  components: {
    listrendering
  }
};
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  text-align: center;
  background: #ffffff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Styling List */
ul {
  list-style: none;
  padding: 0;
  margin-top: 15px;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f8f9fa;
  padding: 12px;
  margin: 6px 0;
  border-radius: 8px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s, background 0.3s;
}

li:hover {
  background: #e3f2fd;
  transform: translateY(-2px);
}

/* Styling Tombol Hapus */
button {
  background: #ff5252;
  color: white;
  border: none;
  padding: 6px 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s;
}

button:hover {
  background: #d32f2f;
}
</style>
