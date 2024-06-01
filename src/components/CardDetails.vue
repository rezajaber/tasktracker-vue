<script setup lang="ts">
import MarkDownLegend from "./MarkDownLegend.vue";
import { Github } from "lucide-vue-next";
import { Button } from "@/components/ui/button";
</script>

<template>
  <div>
    <div class="mx-auto -mt-1 flex w-[22rem] justify-between md:mx-0 md:w-full">
      <a
        href="https://github.com/rezajaber"
        target="_blank"
        rel="noopener noreferrer"
      >
        <Button>
          <Github class="mr-1.5 h-5 w-5" />
          GitHub
        </Button>
      </a>

      <MarkDownLegend />
    </div>
  </div>
</template>
