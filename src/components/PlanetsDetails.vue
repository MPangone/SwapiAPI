<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';
import ListResidents from '../components/ListResidents.vue';

const { id } = useRoute().params;
const planet = ref(null);
const people = ref([]);

onMounted(async () => {
  try {
    const response = await fetch(`https://swapi.dev/api/planets/${id}`);
    const data = await response.json();
    console.log('Response from API:', data);

    if (data.residents) {
      const peoplePromises = await Promise.all(
        data.residents.map(async (residentUrl) => {
          const residentResponse = await fetch(residentUrl);
          return await residentResponse.json();
        })
      );

      people.value = peoplePromises;
    } else {
      console.error('Dados de residentes não encontrados para este planeta.');
    }

    planet.value = data;
  } catch (error) {
    console.error('Erro ao buscar detalhes do planeta:', error);
  }
});
</script>

<template>
  <div>
    <h1>{{ planet ? planet.name : 'Loading...' }}</h1>
    <h2>Residents</h2>
    <div>
        <div class="col-sm-4 col-md-6">
          <div class="card">
            <div class="card-body row">
              <ListResidents
                v-for="person in people"
                :key="person.name"
                :name="person.name"
                :url="`@/img/people/${person.url.split('/').filter(Boolean).pop()}.jpg`"
              />
            </div>
        </div>
      </div>
    </div>
  </div>
</template>