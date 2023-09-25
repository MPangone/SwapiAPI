<script setup>
const { name, url } = defineProps(['name', 'url']);

const goToPlanetDetails = () => {

  const planetId = url.split('/').filter(Boolean).pop();

  const planetDetailsUrl = `/planet/${planetId}`;

  window.open(planetDetailsUrl, '_blank');
};
</script>




<template>
    <div class="col-4">
        <div class="card mb-3">
            <p class="card-title">{{ name }}</p>
            <button  @click="goToPlanetDetails" class="btn btn-primary">See more</button>
            </div>
        </div>
</template>


<style>
</style>