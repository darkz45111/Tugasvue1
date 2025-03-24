<script setup>
import {ref,computed} from 'vue';

const price =ref (0);
const discount =ref(0);

const discountedPrice= computed(()=>{
    return price.value -(price.value*discount.value)/100;
})
</script>

<template>
    <div>
        <h2>hitung harga sesudah diskon</h2>
        <label>harga barang:</label>
        <input type ="number" v-model="price" placeholder="masukkan harga">

        <label>diskon (%):</label>
        <input type ="number" v-model="discount" placeholder="masukkan diskon">

        <p> harga setelah diskon : <strong>{{ discountedPrice }}</strong></p>
    </div>
</template>

<style scoped>
.container{
    max-width: 400px;
    margin: 20px auto;
    font-family: arial,sans-serif;
}
input{
    width: 100%;
    padding: 8px;
    margin: 5px 0;
}
</style>
