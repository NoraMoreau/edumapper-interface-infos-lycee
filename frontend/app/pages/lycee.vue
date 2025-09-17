<template>
<div class="min-h-screen h-full bg-yellow-50">
  <!-- NOM SITE -->
  <div class="p-5 font-bold">
    Edumapper*
  </div>

  <!-- LYCEE -->
  <div v-if="selectedLycee" class=" bg-gradient-to-r from-orange-400 to-pink-400 p-3 border rounded mx-4 mt-4 font-semibold">
    <div class="text-lg">{{ selectedLycee.name }}</div>
    <div class="text-sm opacity-90">{{ selectedLycee.ville }} — {{ selectedLycee.statut }}</div>
    <div class="mt-4 flex items-center justify-between">
        <button @click="modifierLycee()" class="px-4 py-2 bg-white hover:bg-gray-100 rounded-full text-sm">Modifier</button>
    </div>
  </div>

  <!-- CLASSE -->
  <div class="bg-white p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center font-semibold">
        Classe
        <button @click="showClasse = !showClasse" class="text-sm">À compléter</button>
    </div>

    <div v-if="showClasse" class="mt-4 flex gap-2">
      <button 
        @click="selectClasse = 'Seconde'" 
        :class="selectClasse === 'Seconde' ? 'border-black border-4 bg-white' : 'bg-gray-100'" 
        class="px-2 py-1 rounded-full">Seconde</button>
      <button 
        @click="selectClasse = 'Première'" 
        :class="selectClasse === 'Première' ? 'border-black border-4 bg-white' : 'bg-gray-100'" 
        class="px-2 py-1 rounded-full">Première</button>
      <button 
        @click="selectClasse = 'Terminale'" 
        :class="selectClasse === 'Terminale' ? 'border-black border-4 bg-white' : 'bg-gray-100'" 
        class="px-2 py-1 rounded-full">Terminale</button>
    </div>

    <div v-if="showClasse" class="mt-4">Type de bac</div>
    <div v-if="showClasse" class="mt-4 flex gap-2">
      <button 
        @click="selectTypeBac = 'Général'" 
        :class="selectTypeBac === 'Général' ? 'border-black bg-white' : 'bg-gray-100'" 
        class="px-2 py-1 rounded-full">Général</button>
      <button 
        @click="selectTypeBac = 'Technologique'" 
        :class="selectTypeBac === 'Technologique' ? 'border-black bg-white' : 'bg-gray-100'" 
        class="px-2 py-1 rounded-full">Technologique</button>
      <button 
        @click="selectTypeBac = 'Professionel'" 
        :class="selectTypeBac === 'Professionel' ? 'border-black bg-white' : 'bg-gray-100'" 
        class="px-2 py-1 rounded-full">Professionel</button>
    </div>

    <div v-if="showClasse" class="p-3 rounded-full mt-6 justify-between">
        <button 
          class="w-full text-center px-4 py-2 rounded-full" 
          :disabled="!selectClasse || !selectTypeBac"
          :class="!selectClasse || !selectTypeBac ? 'bg-gray-200 cursor-not-allowed text-gray-600' : 'text-white bg-black transition-all'">
          Confirmer
        </button>
    </div>
  </div>

  <!-- SPECIALITE -->
  <div class="bg-white p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center font-semibold">
        Spécialité
        <button @click="aCompleter()" class="text-sm">À compléter</button>
    </div>
  </div>

  <!-- NOTES -->
  <div class="bg-white p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center font-semibold">
        Notes
        <button @click="aCompleter()" class="text-sm">À compléter</button>
    </div>
  </div>
  
  <!-- CONFIRMER LE LYCEE -->
  <div class="fixed bottom-12 left-1/2 transform -translate-x-1/2 font-semibold">
    <button @click="aConfirmer()" class="px-4 py-2 bg-gray-200 rounded-full">Confirmer</button>
  </div>  
</div>
</template>



<script setup>
import { ref, onMounted } from 'vue';
import { lycees } from "@/src/list-lycee";

const selectedLycee = ref(null);
const showClasse = ref(false);
const selectClasse = ref('');
const selectTypeBac = ref('');

onMounted(() => {
  const stored = localStorage.getItem('selectedLycee');
  if (stored) {
    // si on a déjà un lycée stocké, on l'utilise
    selectedLycee.value = JSON.parse(stored);
  } else {
    // sinon, on en prend un au hasard
    const random = lycees[Math.floor(Math.random() * lycees.length)];
    selectedLycee.value = random;
    localStorage.setItem('selectedLycee', JSON.stringify(random));
  }
})

function modifierLycee() {
    window.location.href = '/selection-lycee';
}

</script>