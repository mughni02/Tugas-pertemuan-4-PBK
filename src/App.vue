<script setup>
import { ref } from 'vue';

// 1. Variabel Reaktif dengan ref
const name = ref('');
const count = ref(0);
const isVisible = ref(true);
const imageUrl = ref('https://via.placeholder.com/150');
const textColor = ref('blue');
const status = ref('loading');

// 2. Event Listener
const increment = () => count.value++;
const toggleVisibility = () => isVisible.value = !isVisible.value;
const submitForm = () => alert(`Halo, ${name.value}! Form telah dikirim.`);
</script>

<template>
  <div>
    <!-- 3. Text Interpolation -->
    <h1>Halo, {{ name || 'Pengguna' }}!</h1>

    <!-- 4. Form Binding -->
    <input v-model="name" placeholder="Masukkan nama">
    <button @click="submitForm">Submit</button>

    <!-- 5. Event Listener -->
    <button @click="increment">Klik Saya</button>
    <p>Jumlah Klik: {{ count }}</p>

    <!-- 6. Attribute Binding -->
    <img :src="imageUrl" :alt="'Gambar untuk ' + name">
    <p :style="{ color: textColor }">Teks berwarna</p>

    <!-- 7. Conditional Rendering -->
    <p v-if="status === 'success'">Berhasil!</p>
    <p v-else-if="status === 'loading'">Memuat...</p>
    <p v-else>Gagal!</p>

    <p v-show="isVisible">Teks ini bisa disembunyikan.</p>
    <button @click="toggleVisibility">Tampilkan/Sembunyikan</button>
  </div>
</template>
