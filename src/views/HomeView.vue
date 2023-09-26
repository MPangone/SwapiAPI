<script setup>
import { onMounted, reactive, ref } from 'vue';
import ListPlanets from '../components/ListPlanets.vue';
import '@/main.css';

let planetas = reactive(ref());

onMounted(() => {
  fetch("https://swapi.dev/api/planets/")
  .then(response => response.json())
  .then(response =>{
    planetas.value = response.results;
    console.log(response);
  })
})



</script>

<template>
  <div class="title">
    <h2>Planets</h2> 
  </div>
  <div class="List-planets">
    <div class="row row-cols-3 g-2">  
    <ListPlanets
    v-for="planets in planetas"
    :key="planets.key"
    :name="planets.name"
    :url="planets.url"
    />
    </div>
  </div>          
          
</template>

<style>






</style>
