<script setup>
import { ref, computed } from 'vue'

const name = "Vue 3";

const counter = ref(0); //variable reactiva
const arrayNumeros = ref([]);

const increment = () => counter.value++;

const drecement = () => counter.value--;

const reset = () => (counter.value = 0);

const add = () => arrayNumeros.value.push(counter.value);

const bloquearAdd = computed(() => {
  const numSearch = arrayNumeros.value.find(num => num === counter.value);
  if (numSearch === 0) return true;
  return numSearch ? true : false
})

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  }
  if (counter.value > 0) {
    return 'positive'
  }
  if (counter.value < 0) {
    return 'negative'
  }
});

</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}!</h1>
    <h2 :class="classCounter"> {{ counter }} </h2>

    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="drecement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Resetear</button>
      <button @click="add" :disabled="bloquearAdd" class="btn btn-primary">Añadir</button>
    </div>
    <h2 class="mt-3">Mis Favoritos</h2>
    <ul class="list-group mt-3">
      <li class="list-group-item" v-for="(numero, index) in arrayNumeros" :key="index">
        {{ numero }}
      </li>
    </ul>
  </div>
</template>

<style>
h1 {
  color: red;
}

.positive {
  color: green
}

.negative {
  color: red
}

.zero {
  color: blue
}
</style>


<!-- <script setup>
const name = 'Vue dinamico';
const styleColor = "color: blue";
const arrayColores = ["Blue", "red", "peru"];
const activo = false
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 :style="`color: ${arrayColores[2]}`">Soy jacob</h2>
  <h2 v-if="activo === true">
    <span>*Icono*</span>
    Estoy loco</h2>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>


  <h2 v-show="activo">estoy activo</h2>


  !v-for
  <li v-for="(fruta, index) in arrayFrutas" :key="index">
            {{ fruta }}
        </li

        <script setup>
const name = "Vue 3";
// const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const objetoFruta = {
  name: "Manzana",
  price: "$1.00",
  description: "Una manzana",
  id: 1
}
</script>

<template>
  <h1>Hola {{ name }}!</h1>
  {{ objetoFruta }}
  <ul>
    <li v-for="(value, propiedad, index) in objetoFruta" :key="index" >
      {{ index }} - {{ propiedad }}: {{ value }}
    </li>
  </ul>
</template>

<style>
h1 {
  color: red;
}
</style>


//metodos - methods
const handleClick = (message) =>{
  console.log(message);
}
  <button v-on:click.right.prevent="handleClick('Texto rigth')">Activame right</button>
  <button @click="handleClick('Texto left')">Activame left</button>
  <button @click.middle="handleClick('Texto middle')">Activame middle</button>
</template> -->
