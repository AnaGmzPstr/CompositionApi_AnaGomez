<!-- App vue -->
<template>
  <div class="container">
    <h1>{{ nomComanda }} </h1>
    <input type="text" placeholder="Nom comanda" v-model="nomComanda">
    <Divisa/>
    <Lista/>
  </div>
</template>

<script setup>
import Lista from './components/ListaProd.vue'
import Divisa from './components/Divisa.vue'
import { provide, ref } from 'vue'

const nomComanda = ref("Nom Comanda");

const selectedDivisa = ref('$');
const converionRate = ref(1);

const actualitzarDivisa = (divisa) =>{
  selectedDivisa.value = divisa;
  if (divisa==='$') converionRate.value=1;
  else if (divisa==='€') converionRate.value=0.88;
}

provide('selectedDivisa', selectedDivisa);
provide('converionRate', converionRate);
provide('actualitzarDivisa', actualitzarDivisa);
</script>


<style scoped>
.container{
  display: grid;
  justify-content: center;
  align-items: center;
  border: solid 1px;
  margin: 20px;
}
</style>
