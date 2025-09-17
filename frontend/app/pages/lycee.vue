<template>
  <div class=" bg-blue-100 p-3 border rounded mx-4 mt-4">
    Lycée
    <div class="mt-4">
        <button @click="modifierLycee()" class="px-4 py-2 bg-white rounded-full">Modifier</button>
    </div>
  </div>

  <div class=" bg-blue-100 p-3 border rounded mx-4 mt-4 flex justify-between items-center">
    Classe
    <div>
        <button @click="aCompleter()" class="text-sm">À compléter</button>
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

function modifierLycee() {

}

function aCompleter() {
    
}

function aConfirmer() {

}
</script>