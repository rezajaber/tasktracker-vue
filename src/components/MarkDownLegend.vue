<script setup lang="ts">
import { Button } from "@/components/ui/button";
import { Info } from "lucide-vue-next";

import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";
import Card from "./Card.vue";

const cards = [
  {
    priorityColor: "text-red-500",
    cardCategory: "Cyber Security",
    cardTitle: "Hack The Box",
    cardContent:
      "Explore the latest trends in cybersecurity and learn how to protect your systems effectively.",
    cardDate: "22. September 2024",
  },
];
</script>

<template>
  <div>
    <Dialog>
      <DialogTrigger as-child>
        <Button><Info class="w-5" /> </Button>
      </DialogTrigger>
      <DialogContent
        class="max-h-[90dvh] max-w-xs grid-rows-[auto_minmax(0,1fr)_auto] place-items-center rounded-md p-0 sm:max-w-[425px]"
      >
        <DialogHeader class="p-6 pb-0">
          <DialogTitle>Information - TaskTracker</DialogTitle>
          <DialogDescription
            >Below you can see what everything does and how it is suppose to
            work!</DialogDescription
          >
        </DialogHeader>

        <Card
          v-for="card in cards"
          :key="card.cardTitle"
          :priorityColor="card.priorityColor"
          :cardCategory="card.cardCategory"
          :cardTitle="card.cardTitle"
          :cardContent="card.cardContent"
          :cardDate="card.cardDate"
        />

        <div class="mt-1 grid w-full gap-2 px-6 pb-6 text-sm sm:text-base">
          <p
            class="rounded-md bg-primary px-2.5 py-1 text-center text-sm text-white"
          >
            Click the circle to change the priority of the task.
          </p>

          <p
            class="rounded-md bg-primary px-2.5 py-1 text-center text-sm text-white"
          >
            Click the edit button to add or delete categories.
          </p>

          <p
            class="rounded-md bg-primary px-2.5 py-1 text-center text-sm text-white"
          >
            Click the title to edit it.
          </p>

          <p
            class="rounded-md bg-primary px-2.5 py-1 text-center text-sm text-white"
          >
            Click on the description to edit it.
          </p>

          <p
            class="rounded-md bg-primary px-2.5 py-1 text-center text-sm text-white"
          >
            Click the date icon to change the date.
          </p>

          <p
            class="rounded-md bg-primary px-2.5 py-1 text-center text-sm text-white"
          >
            Click the three dots to delete or mark a task as done.
          </p>
        </div>
      </DialogContent>
    </Dialog>
  </div>
</template>
