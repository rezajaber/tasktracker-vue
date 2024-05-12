<script setup lang="ts">
import { Search } from "lucide-vue-next";
import { CirclePlus } from "lucide-vue-next";
import { SlidersHorizontal } from "lucide-vue-next";

import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
</script>

<template>
  <div class="flex justify-between">
    <div class="flex gap-2">
      <div class="relative w-96 max-w-md items-center">
        <Input
          id="search"
          type="text"
          placeholder="Create or Search for a Task..."
          class="pl-10"
        />
        <span
          class="absolute inset-y-0 start-0 flex items-center justify-center px-3"
        >
          <Search class="w-5 text-muted-foreground" />
        </span>
      </div>

      <Button type="submit"
        ><CirclePlus class="mr-1.5 w-4" />Create Task</Button
      >
    </div>

    <Button type="submit"
      ><SlidersHorizontal class="mr-1.5 w-4" />Filter</Button
    >
  </div>
</template>
