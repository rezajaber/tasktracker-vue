<script setup lang="ts">
import SearchBar from "@/components/SearchBar.vue";
import CardDetails from "@/components/CardDetails.vue";
import Card from "@/components/Card.vue";
</script>

<template>
  <div class="flex h-screen items-center justify-center">
    <div class="grid gap-6">
      <div class="grid gap-2">
        <SearchBar />
        <CardDetails />
      </div>
      <Card />
    </div>
  </div>
</template>
