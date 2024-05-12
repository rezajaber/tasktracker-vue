<script setup lang="ts">
import { Button } from "@/components/ui/button";
import { CalendarClock } from "lucide-vue-next";
import { Info } from "lucide-vue-next";
import { Layers } from "lucide-vue-next";
import { GalleryVerticalEnd } from "lucide-vue-next";
</script>

<template>
  <div>
    <div class="flex justify-between">
      <div class="flex gap-2">
        <Button type="submit"
          ><GalleryVerticalEnd class="mr-1.5 w-5" />Priority</Button
        >
        <Button type="submit"><Layers class="mr-1.5 w-5" />Category</Button>
      </div>

      <div class="flex gap-2">
        <Button type="submit"><CalendarClock class="mr-1.5 w-5" />Date</Button>
        <Button type="submit"><Info class="mr-1.5 w-5" />Infos</Button>
      </div>
    </div>
  </div>
</template>
