<script setup>
import { reactive, computed, ref } from "vue";
const novoItem = ref("");

const cidades = reactive([
  "São Paulo",
  "Rio de Janeiro",
  "Belo Horizonte",
  "Salvador",
  "Fortaleza",
  "Curitiba",
  "Manaus",
  "Recife",
  "Porto Alegre",
  "Brasília",
]);
const cidadesOrdenadas = computed(() => {
  return cidades.slice().sort((a, b) => a.localeCompare(b));
});
function adicionarOrdenado() {
  cidades.push(novoItem.value);
  cidades.sort((a, b) => a.localeCompare(b));
  novoItem.value = "";
}
function keycode() {
  adicionarOrdenado();
}
</script>
<template>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap"
    rel="stylesheet"
  />

  <div class="container">
    <link rel="stylesheet" href="./css/style.css" />
    <p class="itens" v-for="(item, index) in cidadesOrdenadas" :key="index">
      {{ item }}
    </p>
    <input
      class="input"
      type="text"
      v-model="novoItem"
      @keyup.enter="adicionarOrdenado"
    />
    <button class="button" type="submit">Adicionar</button>
  </div>
</template>
<style lang="scss" scoped>
@import "./css/style.css";
</style>