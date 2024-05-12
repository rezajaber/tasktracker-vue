<script setup lang="ts">
import Card from "@/components/Card.vue";
import SearchBar from "@/components/SearchBar.vue";
</script>

<template>
  <div class="flex h-screen items-center justify-center">
    <div class="grid gap-6">
      <SearchBar />
      <Card />
    </div>
  </div>
</template>
