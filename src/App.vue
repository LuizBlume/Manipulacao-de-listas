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
  if (event.keyCode === 13) {
    adicionar();
  }
}
</script>
<template>
  <div class="container">
    <link rel="stylesheet" href="./css/style.css">
    <p class="itens" v-for="(item, index) in cidadesOrdenadas" :key="index">{{ item }}</p>
    <input class="inpt" type="text" v-model="novoItem" />
    <button class="button" type="submit" @click="adicionarOrdenado">Adicionar</button>
  </div>
</template>
<style lang="scss" scoped>
@import "./css/style.css";
</style>
