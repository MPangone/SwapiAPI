<script setup>
import '@/main.css';
const { name, url } = defineProps(['name', 'url']);

const getImagePath = (id) => {
  return `/img/people/${id}`; 
};

const imagePath = getImagePath(url.split('/').filter(Boolean).pop());

</script>

<template>
<div class="col"  style="width: 15rem;">
  <div class="card h-100">
      <img id="fotopersonagens" :src="imagePath" class="card-img-top" alt="">
      <div class="card-body">
      <h5 class="card-title">{{ name }}</h5>
  </div>
  </div>
</div>
</template>

