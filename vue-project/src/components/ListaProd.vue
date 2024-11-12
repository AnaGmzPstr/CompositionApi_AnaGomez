<template>
    <h3>Productes disponibles</h3>
    <ul 
    v-for="(product, index) in productos"
    :key="index"
    >
    <li>
        <p>{{ product.name }} - Preu: {{ product.price }} {{ selectedDivisa }}</p>
        <button @click="afegir(product.name, product.price)">Afegir</button>
    </li>
    </ul>
    <button @click="mostrarCarrito">Ver mis productos</button>

</template>

<script setup>

import { inject, watch } from 'vue';

const selectedDivisa = inject('selectedDivisa');
const converionRate = inject('converionRate');

const productos = [
    { name: "Hamburger 🍔", price: 5 },
    { name: "Cheeseburger 🧀", price: 6 },
    { name: "Impossible Burger (vegana)🤮", price: 7 },
    { name: "Fries 🍟", price: 2 }
];

const arrayCompra=[];

function afegir(nom, preu){
    let articulo = `${nom} - ${preu} ${selectedDivisa.value} `
    arrayCompra.push(articulo);
}

function mostrarCarrito(){
    if (arrayCompra.length===0) alert("La teva comanda està buida");
    else alert(arrayCompra.toString());
}

const converionPreu = (price) => (price * converionRate.value).toFixed(2);

watch(selectedDivisa, onSelectedDivisa);

function onSelectedDivisa(){
    console.log(selectedDivisa.value);
    if (selectedDivisa.value=="€"){
        for (let i in productos){
            productos[i].price = (productos[i].price * 0.88).toFixed(2);
            console.log(productos[i].price)
        }
        
    } else if (selectedDivisa.value=='$'){
        for (let i in productos){
            productos[i].price = (productos[i].price / 0.88).toFixed(2);
        }
    }
}

</script>

<style>
li{
    list-style: none;
}
</style>