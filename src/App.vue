
<script setup>
import { ref,computed } from 'vue';

const name = ref('');
const count = ref(0);
const inputValue = ref(1) // Default input value 1
const maxLimit = ref(10)
const isVisible = ref(true);
const textColor = ref('blue');
const status = ref('loading');

const isEven = computed(() => count.value % 2 === 0)
const multipliedCount = computed(() => count.value * 2)

const toggleVisibility = () => isVisible.value = !isVisible.value;
// Methods
function increment() {
  if (count.value + inputValue.value <= maxLimit.value) {
    count.value += inputValue.value
  }
}

function decrement() {
  if (count.value - inputValue.value >= 0) {
    count.value -= inputValue.value
  }
}

function hapus() {
  count.value = 0
  inputValue.value = 1
}
</script>

<style scoped>
button {
  padding: 8px 12px;
  border: 1px solid black;
  background-color: burlywood;
  cursor: pointer;
}

button:hover {
  background-color: lightgray;
}
</style>


<template>
  <div>
    <h1>Welcome, {{ name || '' }}!</h1>
    <h3 style="color: blue;">NILAI COUNT: {{ count }}</h3>
    <p v-if="count === 0" style="color: green;">Count masih nol.</p>
    <p v-else-if="count >= maxLimit" style="color: orange;">Batas maksimum tercapai!</p>
    <p v-else>Count dalam batas normal</p>
    <p>Genap : {{ isEven ? 'Ya' : 'Tidak' }}</p>
    <p>Perkalian count dengan 2: {{ multipliedCount }}</p>
    <input v-model="name" placeholder="Masukkan nama">
    <input v-model.number="inputValue" type="number" style="width: 50px; text-align: center; margin-right: 10px;">
    <button @click="increment">Tambah</button>
    <button @click="decrement" style="margin-left: 10px;">Kurang</button>
    <button @click="hapus" style="margin-left: 10px;">Hapus </button>

    <p v-show="isVisible">Teks ini bisa disembunyikan.</p>
    <button @click="toggleVisibility">Tampilkan/Sembunyikan</button>
  </div>
</template>
