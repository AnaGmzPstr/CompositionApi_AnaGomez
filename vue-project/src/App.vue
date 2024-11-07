<!-- App vue -->
<script setup>
import Lista from './components/ListaProd.vue'
import { ref } from 'vue'
const nomComanda = ref("");
</script>

<template>
  <div class="container">
    <h1>{{ nomComanda }} </h1>
    <input type="text" placeholder="Nom comanda" v-model="nomComanda">
    <Lista/>
  </div>
</template>

<style scoped>
.container{
  display: grid;
  justify-content: center;
}
</style>
