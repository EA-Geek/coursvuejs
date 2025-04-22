<template>
  <div class="App_cont">
    <h1>Travail pratique de TODOLIST</h1>
    <div>
      <form @submit.prevent="AddTache">
        <input
          type="text"
          placeholder="Ajouter une tache"
          v-model="AjoutTache"
        />
        <button>Ajouter</button>
      </form>
    </div>
    <div>
      <ul>
        <li v-for="Tache in ListTache" :key="Tache">
          {{ Tache }}<button @click="DeleteTache(Tache)">Supprimer</button>
          <input type="checkbox" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const ListTache = ref(["Prendre le lait", "Prendre le the", "Prendre le cafe"]);
const AjoutTache = ref("");
const AddTache = () => {
  if (AjoutTache.value === "") {
    alert("Veuiller entre une tache valide");
    return;
  } else if (ListTache.value.includes(AjoutTache.value)) {
    alert("Tache deja selectionner");
    return;
  }
  AjoutTache.value = ListTache.value.unshift(AjoutTache.value);
  AjoutTache.value = "";
};
const DeleteTache = (Tache) => {
  ListTache.value = ListTache.value.filter((m) => m != Tache);
};
</script>

<style>
* {
  font-family: Arial, Helvetica, sans-serif;
}
h1 {
  text-align: center;
}
form {
  display: flex;
  justify-content: center;
  align-items: center;
}
form input {
  width: 60%;
  height: 40px;
  margin: 5px;
  border-radius: 5px;
  border: 1px solid black;
}
form button {
  width: 150px;
  height: 40px;
  border-radius: 5px;
  border: 1px solid black;
  cursor: pointer;
}
li {
  list-style: none;
  margin: 10px;
  border: 1px solid black;
  padding: 10px;
}
li button {
  height: 30px;
  width: 100px;
  background-color: red;
  border: none;
  border-radius: 5px;
  top: 0;
  left: 300px;
  position: relative;
}
li input {
  top: 0;
  left: 330px;
  position: relative;
}
</style>
