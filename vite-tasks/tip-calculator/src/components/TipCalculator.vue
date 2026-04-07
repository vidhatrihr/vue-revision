<script setup>
import { ref, computed } from 'vue';

const billAmount = ref(100);
const numOfPeople = ref(5);
const tipPercent = ref(10);
console.log(tipPercent);

const tipAmount = computed(() => (billAmount.value * tipPercent.value) / 100);
const totalAmount = computed(() => billAmount.value + tipAmount.value);
const perPerson = computed(() => {
  if (numOfPeople.value == 0 || billAmount.value == 0) return '-';
  return (totalAmount.value / numOfPeople.value).toFixed(2);
});
</script>

<template>
  <data class="info-card">
    <label>
      Bill Amount:
      <input type="number" v-model="billAmount" />
    </label>

    <label>
      Number of People:
      <input type="number" v-model="numOfPeople" />
    </label>
  </data>

  <div class="btn-card">
    <button @click="tipPercent = 10" :class="{ active: tipPercent === 10 }">10%</button>

    <button @click="tipPercent = 15" :class="{ active: tipPercent === 15 }">15%</button>

    <button @click="tipPercent = 20" :class="{ active: tipPercent === 20 }">20%</button>
  </div>

  <div>Tip Amount: {{ tipAmount }}</div>
  <div>Total Amount: {{ totalAmount }}</div>
  <div>Per Person: {{ perPerson }}</div>
</template>

<style scoped>
button {
  margin: 1rem;
  padding: 0.25rem;
  width: 150px;
  height: 50px;
}

.info-card {
  display: flex;
  flex-direction: column;
}

input {
  padding: 0.5rem;
}

.active {
  border: 1px, solid, green;
  color: black;
  background-color: rgb(79, 138, 79);
}
</style>
