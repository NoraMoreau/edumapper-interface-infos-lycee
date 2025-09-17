<template>
  <!-- LYCEE -->
  <div class=" bg-blue-100 p-3 border rounded mx-4 mt-4 font-semibold">
    {{ selectedLycee }}
    <div class="mt-4 flex items-center justify-between">
        <button @click="modifierLycee()" class="px-4 py-2 bg-white rounded-full text-sm">Modifier</button>
    </div>
  </div>

  <!-- CLASSE -->
  <div class="bg-blue-100 p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center font-semibold">
        Classe
        <button @click="showClasse = !showClasse" class="text-sm">À compléter</button>
    </div>

    <div v-if="showClasse" class="mt-4 flex gap-2">
      <button 
        @click="selectClasse = 'Seconde'" 
        :class="selectClasse === 'Seconde' ? 'bg-blue-300' : 'bg-white'" 
        class="px-2 py-1 rounded-full">Seconde</button>
      <button 
        @click="selectClasse = 'Première'" 
        :class="selectClasse === 'Première' ? 'bg-blue-300' : 'bg-white'" 
        class="px-2 py-1 rounded-full">Première</button>
      <button 
        @click="selectClasse = 'Terminale'" 
        :class="selectClasse === 'Terminale' ? 'bg-blue-300' : 'bg-white'" 
        class="px-2 py-1 rounded-full">Terminale</button>
    </div>

    <div v-if="showClasse" class="mt-4">Type de bac</div>
    <div v-if="showClasse" class="mt-4 flex gap-2">
      <button 
        @click="selectTypeBac = 'Général'" 
        :class="selectTypeBac === 'Général' ? 'bg-blue-300' : 'bg-white'" 
        class="px-2 py-1 rounded-full">Général</button>
      <button 
        @click="selectTypeBac = 'Technologique'" 
        :class="selectTypeBac === 'Technologique' ? 'bg-blue-300' : 'bg-white'" 
        class="px-2 py-1 rounded-full">Technologique</button>
      <button 
        @click="selectTypeBac = 'Professionel'" 
        :class="selectTypeBac === 'Professionel' ? 'bg-blue-300' : 'bg-white'" 
        class="px-2 py-1 rounded-full">Professionel</button>
    </div>

    <div v-if="showClasse" class="p-3 rounded-full mt-6 justify-between">
        <button 
          class="w-full text-center px-4 py-2 rounded-full" 
          :disabled="!selectClasse || !selectTypeBac"
          :class="!selectClasse || !selectTypeBac ? 'bg-gray-200 cursor-not-allowed' : 'bg-gray-200 hover:bg-gray-100'">
          Confirmer
        </button>
    </div>
  </div>

  <!-- SPECIALITE -->
  <div class="bg-blue-100 p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center font-semibold">
        Spécialité
        <button @click="aCompleter()" class="text-sm">À compléter</button>
    </div>
  </div>

  <!-- NOTES -->
  <div class="bg-blue-100 p-3 border rounded mx-4 mt-4">
    <div class="flex justify-between items-center font-semibold">
        Notes
        <button @click="aCompleter()" class="text-sm">À compléter</button>
    </div>
  </div>
  
  <!-- CONFIRMER LE LYCEE -->
  <div class="fixed bottom-12 left-1/2 transform -translate-x-1/2 font-semibold">
    <button @click="aConfirmer()" class="px-4 py-2 bg-gray-200 rounded-full">Confirmer</button>
  </div>  
</template>



<script setup>
import { ref, onMounted } from 'vue';

const selectedLycee = ref('Lycée Gaston Berger');
const showClasse = ref(false);
const selectClasse = ref('');
const selectTypeBac = ref('');

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