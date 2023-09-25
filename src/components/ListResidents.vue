<script setup>
import '@/main.css';
const { name, url } = defineProps(['name', 'url']);

const getImagePath = (id) => {
  return `/img/people/${id}`; 
};

const imagePath = getImagePath(url.split('/').filter(Boolean).pop());

</script>

<template id="personagens-card">
<div class="row row-cols-1 row-cols-md-3 g-5">
  <div class="col">
  <div class="card">
    <img :src="imagePath" class="card-img-top" :alt="name">
    <div class="card-body">    
      <p class="card-title">{{ name }}</p>
      <p class="card-text">teste</p>
    </div>
  </div>
</div>
</div>
</template>

