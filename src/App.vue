<template>
  <div class="App_cont">
    <div>
      <div>
        <p v-hide="counter > 5">Test v-hide</p>
      </div>
      <div v-if="counter < 5" style="color: red">
        <p>Vous avez clicker moins de 5 fois</p>
      </div>
      <div v-else style="color: green">
        <p>Vous avez clicker plus de 5 fois</p>
      </div>
    </div>
    <h1>Je suis un compteur : {{ counter }}</h1>
    <button @click="increment">Incrementer le compteur</button>
    <button @click="decrementer">Decrementer</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const counter = ref(0);

const increment = () => {
  counter.value++;
};

const decrementer = () => {
  counter.value--;
};
</script>

<style>
/*  */
</style>
