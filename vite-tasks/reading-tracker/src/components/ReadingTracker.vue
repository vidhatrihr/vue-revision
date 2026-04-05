<script setup>
import { ref, computed } from 'vue';

const bookTitle = ref('');
const currentPage = ref('-');
const totalPages = ref('-');

const progressPercent = computed(() =>
  Math.round((currentPage.value / totalPages.value) * 100),
);
</script>

<template>
  <div class="input-card">
    <label>
      Book Title:
      <input type="text" v-model="bookTitle" />
    </label>

    <label>
      Current Page:
      <input type="number" v-model="currentPage" />
    </label>

    <label>
      Total Pages:
      <input type="number" v-model="totalPages" />
    </label>
  </div>

  <div :style="{ width: progressPercent + '%', backgroundColor: 'lightblue' }">
    {{ progressPercent }}
  </div>
</template>

<style scoped>
.input-card {
  display: flex;
  gap: 1rem;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.progress-bar {
  background-color: white;
  color: white;
}

input {
  padding: 0.5rem;
}

div {
  margin: 1rem;
  padding: 0.5rem;
}
</style>
