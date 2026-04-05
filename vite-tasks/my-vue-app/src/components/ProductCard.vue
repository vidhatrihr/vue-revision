<script setup>
import { ref, computed } from 'vue';

const productName = ref('Gaming Laptop');
const price = ref(200);
const inStock = ref(true);
const quantity = ref(1);
const cartCount = ref(0);

const stockLabel = computed(() => (inStock.value ? 'In Stock' : 'Out of Stock'));

const totalPrice = computed(() => price.value * quantity.value);

const increase = () => {
  if (quantity.value < 10) quantity.value++;
};

const decrease = () => {
  if (quantity.value > 1) quantity.value--;
};

const addToCart = () => {
  cartCount.value += quantity.value;
};
</script>

<template>
  <div>
    <div>Cart: {{ cartCount }} item(s)</div>
  </div>

  <h2>{{ productName }}</h2>
  <p>${{ price }}</p>

  <p :class="inStock ? 'in-stock' : 'out-of-stock'">
    {{ stockLabel }}
  </p>

  <div>
    <button @click="decrease">-</button>
    <span>{{ quantity }}</span>
    <button @click="increase">+</button>
  </div>

  <p>Total: ${{ totalPrice }}</p>

  <button :disabled="!inStock" @click="addToCart">Add to Cart</button>
</template>
