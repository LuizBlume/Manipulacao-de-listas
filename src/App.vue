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
function adicionar() {
  cidades.push(novoItem.value);
  novoItem.value = "";
}
</script>
<template>
  <div>
    <p v-for="(item, index) in cidades" :key="index">{{ item }}</p>
    <input type="text" v-model="novoItem" />
    <button @click="adicionar">Adicionar</button>
  </div>
</template>
