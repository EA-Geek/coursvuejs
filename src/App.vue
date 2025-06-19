<template>
  <div class="App_cont">
    <h1>Welcome to My Vue App</h1>
    <h2>Movie Management</h2>
    <p>Add Movie favorite :</p>
    <form @submit.prevent="addMovie">
      <input type="text" v-model="newMovie" placeholder="Enter movie name" />
      <button type="submit">Ajouter</button>
    </form>
    <h2>Movie List</h2>
    <ul>
      <li v-for="movie in ListMovies" :key="movie">
        {{ movie }} <button @click="deleteMovies(movie)">Supprimer</button>
      </li>
    </ul>
  </div>
  <div>
    <button @click="sortMovies">Organiser</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const ListMovies = ref(["Matrix", "Lilo", "Stich", "Avatar", "Titanic"]);

const newMovie = ref("");

const addMovie = () => {
  if (newMovie.value.trim() === "") {
    alert("Please enter a movie name.");
    return;
  }
  if (ListMovies.value.includes(newMovie.value)) {
    alert("This movie is already in the list.");
    return;
  }
  if (newMovie.value.length < 3) {
    alert("Movie name must be at least 3 characters long.");
    return;
  }
  ListMovies.value.push(newMovie.value);
  newMovie.value = "";
};

const deleteMovies = (movie) => {
  ListMovies.value = ListMovies.value.filter((m) => m !== movie);
};

const sortMovies = () => {
  ListMovies.value.sort((a, b) => (a > b ? 1 : -1));
};
</script>

<style>
/*  */
</style>
