<template>
  <div class="p-4 mx-4 mt-4">
    <input
      type="text"
      v-model="search"
      placeholder="Rechercher un lycée..."
      class="w-full p-3 border rounded mb-4"
    />

    <ul v-if="search">
      <li
        v-for="lycee in filteredLycees"
        :key="lycee.id"
        @click="selectLycee(lycee)"
        class="p-3 border rounded mb-2 hover:bg-blue-100 cursor-pointer"
      >
        {{ lycee.name }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const lycees = ref([
  { id: 1, name: 'Etienne Dolet' },
  { id: 2, name: 'Lycée privé Charles de Foucauld' },
  { id: 3, name: 'Lycée polyvalent Guillaume Tirel' },
  { id: 4, name: 'Lycée polyvalent l\'Initiative' },
  { id: 5, name: 'Lycée polyvalent privé Saint Jean de Montmartre' },
  { id: 6, name: 'Lycée privé Pascal' },
  { id: 7, name: 'Lycée du bâtiment et des travaux publics' },
  { id: 8, name: 'Lycée polyvalent privé Saint-Nicolas' },
  { id: 9, name: 'Lycée privé La Rochefoucauld' },
  { id: 10, name: 'Lycée technique privé de l\'école technique supérieure du laboratoire' },
  { id: 11, name: 'Lycée privé Charles Péguy' },
  { id: 12, name: 'Lycée privé Sainte-Louise' },
  { id: 13, name: 'Lycée privé L\'Ecole alsacienne' },
  { id: 14, name: 'Lycée polyvalent ESAA-Ecole Boulle' },
  { id: 15, name: 'Lycée polyvalent Paul Poiret' },
  { id: 16, name: 'Lycée Charlemagne' },
  { id: 17, name: 'Lycée Claude Monet' },
  { id: 18, name: 'Lycée privé Lucien de Hirsch' },
  { id: 19, name: 'Lycée privé Saint-Michel de Picpus' }
])

const search = ref('')

const filteredLycees = computed(() =>
  lycees.value.filter(l => l.name.toLowerCase().includes(search.value.toLowerCase()))
)

const selectLycee = (lycee) => {
  localStorage.setItem('selectedLycee', JSON.stringify(lycee))
  router.push('/lycee')
}
</script>