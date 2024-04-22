<script setup lang="ts">
import { onMounted, ref } from 'vue'
import PageHeader from './components/PageHeader.vue';
import axiosClient from "./utils/axios"

// lo ultimo. primero dejo el array vacio y más adelante lo tipo
const paises = ref<pais[]>([])
// primero esto 
const fetchCountries = async() => {
  const { data } = await axiosClient.get("/all");
  paises.value = data; 
}
onMounted(() => {
  fetchCountries();
})

interface pais {
   name:{
    common: string
}
}

</script>

<template>
<PageHeader />
<div v-for="pais in paises">{{ pais.name.common }}</div>
</template>


