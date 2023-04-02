<script setup>
import { ref } from 'vue';
import EntryItem from './EntryItem.vue'

const entries = ref([]);
async function getData() {
    const res = await fetch("http://localhost:5000/api/entries/12/0");
    const finalRes = await res.json();
    entries.value = finalRes;
}
getData()
</script>

<template>
    <div class="container">
      <div v-for="entry in entries" :key="entry.id">
        <EntryItem>
          <img :src="entry.image" />
          <template #colorway>{{ entry.colorway }}</template>
          <template #sculpt>{{ entry.display_name }}</template>
          <template #clw_num>{{ entry.clw_num }}</template>
          <template #clw_total>{{ entry.clw_total }}</template>
        </EntryItem>
      </div>
    </div>
  </template>