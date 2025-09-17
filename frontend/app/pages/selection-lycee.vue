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
import { ref, computed } from 'vue';
import { useRouter } from 'vue-router';
import { lycees } from "@/src/list-lycee";

const router = useRouter()
const search = ref('')

const filteredLycees = computed(() =>
  lycees.value.filter(l => l.name.toLowerCase().includes(search.value.toLowerCase()))
)

const selectLycee = (lycee) => {
  localStorage.setItem('selectedLycee', JSON.stringify(lycee))
  router.push('/lycee')
}
</script>