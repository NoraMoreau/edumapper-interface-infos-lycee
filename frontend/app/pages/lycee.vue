<template>
  <div class=" bg-blue-100 p-3 border rounded mx-4 mt-4">
    {{ selectedLycee }}
    <div class="mt-4 flex items-center justify-between">
        <button @click="modifierLycee()" class="px-4 py-2 bg-white rounded-full">Modifier</button>
    </div>
  </div>

  <div class="bg-blue-100 p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center">
        Classe
        <button @click="showClasse = !showClasse" class="text-sm">À compléter</button>
    </div>

    <div v-if="showClasse" class="mt-2 flex gap-2">
      <button class="px-2 py-1 bg-white rounded mr-2">Seconde</button>
      <button class="px-2 py-1 bg-white rounded mr-2">Première</button>
      <button class="px-2 py-1 bg-white rounded">Terminale</button>
    </div>
  </div>

  <div class=" bg-blue-100 p-3 border rounded mx-4 mt-4 flex justify-between items-center">
    Spécialité
    <div>
        <button @click="aCompleter()" class="text-sm">À compléter</button>
    </div>
  </div>

  <div class=" bg-blue-100 p-3 border rounded mx-4 mt-4 flex justify-between items-center">
    Notes
    <div>
        <button @click="aCompleter()" class="text-sm">À compléter</button>
    </div>
  </div>
  
  <div class="fixed bottom-12 left-1/2 transform -translate-x-1/2">
    <button @click="aConfirmer()" class="px-4 py-2 bg-gray-200 rounded-full">Confirmer</button>
  </div>  
</template>

<script setup>
import { ref, onMounted } from 'vue';

const selectedLycee = ref('Lycée Gaston Berger');
const showClasse = ref(false);
const classes = ['Seconde', 'Première', 'Terminale'];

onMounted(() => {
  const stored = localStorage.getItem('selectedLycee')
  if (stored) {
    selectedLycee.value = JSON.parse(stored).name
  }
});

function modifierLycee() {
    window.location.href = '/selection-lycee';
}

function aCompleter() {
    
}

function aConfirmer() {

}
</script>