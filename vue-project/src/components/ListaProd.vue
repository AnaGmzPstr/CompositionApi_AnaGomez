<template>
    <h3>Productes disponibles</h3>
    <ul 
    v-for="(product, index) in productos"
    :key="index"
    >
    <li>
        <p>{{ product.name }} - Preu: {{ converionPreu(product.price) }} {{ selectedDivisa }}</p>
        <button @click="afegir">Afegir</button>
    </li>
    </ul>

</template>

<script setup>
import { inject } from 'vue';

const selectedDivisa = inject('selectedDivisa');
const converionRate = inject('converionRate');

const productos = [
    { name: "Hamburger 🍔", price: 5 },
    { name: "Cheeseburger 🧀", price: 6 },
    { name: "Impossible Burger (vegana)🤮", price: 7 },
    { name: "Fries 🍟", price: 2 }
];

const converionPreu = (price) => (price * converionRate.value).toFixed(2);
</script>

<style>
li{
    list-style: none;
}
</style>