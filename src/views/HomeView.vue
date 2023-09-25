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
  <main>
    <div class="container">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <div class="card" style="width: 18rem;">
          <!--div class="card mb-3" style="width: 31rem;"--> 
            <img src="https://raw.githubusercontent.com/jendang/star-wars-api/master/starwarslogo.png" class="card-img-top" alt="...">
            <div class="card-body">
            <h5 class="card-title">StarWars</h5>
            <p class="card-text">Just a project</p>
            <a href="https://www.starwars.com/" target="_blank" class="btn btn-primary">About StarWars</a>
        </div>
        </div>
        </div>
        <div class="col-sm-12 col-md-6">
          <div class="card">
            <div class="card-body row">
              <ListPlanets
              v-for="planets in planetas"
              :key="planets.key"
              :name="planets.name"
              :url="planets.url"
              />
            </div>
          </div> 
        </div>    
      </div>
    </div>
  </main>
</template>

<style>






</style>
