<template>
  <div id="app">
    <h1 :class="{ 'highlight': isHighlighted }">{{ message }}</h1>
    <p :style="{color: textColor, fontSize: textSize }">Klik tombol shazam maka warna teks ini akan berubah:</p>
    <input type="text" v-model="inputText" @input="updateMessage">
    <button @click="toggleHighlight">shazam</button>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  setup() {
    const message = ref('shazaaaaaam');
    const isHighlighted = ref(false);
    const inputText = ref('');
    const textColor = computed(() => isHighlighted.value ? 'yellow' : 'black');
    const textSize = ref('27px'); // Ukuran font awal

    function updateMessage() {
      message.value = inputText.value;
    }

    function toggleHighlight() {
      isHighlighted.value = !isHighlighted.value;
      // Ubah ukuran font saat toggle
      textSize.value = isHighlighted.value ? '27px' : '27px';
    }

    return {
      message,
      isHighlighted,
      inputText,
      textColor,
      textSize,
      updateMessage,
      toggleHighlight
    };
  }
}
</script>

<style scoped>
/* Scoped styles for component */
h1 {
  color: #ff0000;
  font-family: 'stencil', sans-serif;
}
p {
  font-family: stencil;
  color: #fbff00;
}
</style>
