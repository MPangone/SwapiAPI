<script setup>
const { name, url } = defineProps(['name', 'url']);
const goToPlanetDetails = () => {

  const planetId = url.split('/').filter(Boolean).pop();

  const planetDetailsUrl = `/planet/${planetId}`;

  window.open(planetDetailsUrl, '_blank');
};

const getImagePath = (id) => {
  return `/img/planets/${id}.jpg`; 
};

const imagePath = getImagePath(url.split('/').filter(Boolean).pop());
</script>




<template>
  <div class="col"  style="width: 16rem;">
    <div style="margin-top: 3rem; " class="card h-100">
      <img :src="imagePath" class="card-img-top fixed-image" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ name }}</h5>
        <a @click="goToPlanetDetails" class="btn btn-primary">See more</a>
      </div>
    </div>
  </div>
</template>


<style>
.fixed-image{
  width: auto;
  height: 150px;
}
</style>