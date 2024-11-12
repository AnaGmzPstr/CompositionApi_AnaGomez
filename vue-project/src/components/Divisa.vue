<template>
    <div>
        <select name="divisa" id="divisa" @change="selectDivisa($event)">
            <option value="€">Euros (€)</option>
            <option value="$" selected>Dólares ($)</option>
        </select>
    </div>
</template>

<script setup>
import { inject } from 'vue';

const actualitzarDivisa = inject('actualitzarDivisa');

const selectDivisa = (event) =>{
    const selected = event.target.value;
    actualitzarDivisa(selected);
}

</script>