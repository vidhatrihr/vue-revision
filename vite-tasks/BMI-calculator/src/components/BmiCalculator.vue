<script setup>
import { ref, computed } from 'vue';

const height = ref(150); // cm
const weight = ref(60); // kg

const bmi = computed(() => (weight.value / (height.value / 100) ** 2).toFixed(2));

const bmiCategory = computed(() => {
  if (bmi.value < 18.5) return 'UnderWeight';
  else if (bmi.value >= 18.5 && bmi.value <= 24.9) return 'Normal';
  else if (bmi.value >= 25 && bmi.value <= 29.9) return 'OverWeight';
  else if (bmi.value >= 30) return 'Obese';
});
</script>

<template>
  <div>
    <form>
      <label>
        Weight (kg):
        <input type="number" v-model="weight" />
      </label>
      <br />
      <label>
        Height (cm):
        <input type="number" v-model="height" />
      </label>
    </form>

    <div>BMI: {{ bmi }}</div>
    <div :class="`${bmiCategory}`">Category: {{ bmiCategory }}</div>
  </div>
</template>

<style scoped>
.UnderWeight,
.OverWeight {
  color: orange;
}
.Normal {
  color: green;
}

.Obese {
  color: red;
}
</style>
