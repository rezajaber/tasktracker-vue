<script setup lang="ts">
import { Circle } from "lucide-vue-next";
import { CalendarClock } from "lucide-vue-next";
import { Ellipsis } from "lucide-vue-next";
import { ListChecks } from "lucide-vue-next";
import { Trash2 } from "lucide-vue-next";

import { Separator } from "@/components/ui/separator";

import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuRadioGroup,
  DropdownMenuRadioItem,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";

const cards = [
  {
    color: "text-red-500",
    category: "Cyber Security",
    title: "Hack The Box",
    content:
      "Explore the latest trends in cybersecurity and learn how to protect your systems effectively.",
    date: "22. September 2024",
  },
  {
    color: "text-blue-500",
    category: "Data Analysis",
    title: "Do not miss the Data",
    content:
      "Deep dive into data analysis techniques that can transform your business insights.",
    date: "30. October 2024",
  },
  {
    color: "text-green-500",
    category: "Renewable Energy",
    title: "Tesla or Xiaomi",
    content:
      "Renewable energy solutions are becoming more affordable and accessible, driving sustainability.",
    date: "15. November 2024",
  },
  {
    color: "text-yellow-500",
    category: "Digital Marketing",
    title: "Zahlungswerk to the Top",
    content:
      "Understanding the digital marketing landscape is crucial for any modern business strategy.",
    date: "05. December 2024",
  },
  {
    color: "text-purple-500",
    category: "AI Development",
    title: "ChatGPT - Dangerous?",
    content:
      "Artificial intelligence continues to evolve, offering new possibilities in various sectors.",
    date: "10. January 2025",
  },

  {
    color: "text-orange-500",
    category: "Healthcare Innovation",
    title: "AI-Doctors rule the world",
    content:
      "Innovative healthcare technologies are revolutionizing patient care worldwide.",
    date: "25. February 2025",
  },
  /*{
    color: "text-pink-500",
    category: "Education Technology",
    title: "New IPad-OS helps student",
    content:
      "The impact of technology on education is profound, shaping the future of learning.",
    date: "20. March 2025",
  },
  {
    color: "text-gray-500",
    category: "Industry 4.0",
    title: "Xiaomi Robots",
    content:
      "The fourth industrial revolution brings smart technology to manufacturing and production.",
    date: "15. April 2025",
  },
  {
    color: "text-indigo-500",
    category: "Blockchain",
    title: "Bitcoin over Etherum Bitcoin over EtherumBitcoin over Etherum",
    content:
      "Blockchain technology promises enhanced security and transparency in digital transactions.",
    date: "05. May 2025",
  },*/
];
</script>

<template>
  <div class="grid grid-cols-3 gap-5">
    <!-- FULL CARD -->
    <div
      v-for="card in cards"
      :key="card.title"
      class="card-container grid-rows-layout grid gap-3.5 rounded-lg p-5"
    >
      <!-- HEADER OF CARD -->
      <div class="flex items-center gap-2">
        <Circle :class="`h-3 w-3 ${card.color} fill-current`" />
        <span class="font-medium">{{ card.category }}</span>
      </div>

      <!-- BODY OF CARD -->
      <div class="-mt-1 flex flex-col gap-1">
        <h1 class="line-clamp-1 text-lg font-semibold">{{ card.title }}</h1>
        <span class="line-clamp-3 text-sm">{{ card.content }}</span>
      </div>

      <Separator class="w-full bg-gray-500" />

      <!-- FOOTER OF CARD -->
      <div class="flex items-center justify-between">
        <div class="flex items-center gap-2">
          <CalendarClock class="h-5 w-5" />
          <span class="text-sm">{{ card.date }}</span>
        </div>

        <DropdownMenu>
          <DropdownMenuTrigger as-child>
            <Button>
              <Ellipsis
                class="h-6 w-6 cursor-pointer duration-300 ease-in-out hover:rotate-90"
              />
            </Button>
          </DropdownMenuTrigger>
          <DropdownMenuContent class="grid w-40 gap-1 px-3 py-2">
            <div
              class="flex cursor-pointer items-center gap-2 duration-300 ease-in-out hover:scale-105"
            >
              <ListChecks class="w-5 text-green-600" />
              <span class="text-sm">Task Done</span>
            </div>
            <div
              class="flex cursor-pointer items-center gap-2 duration-300 ease-in-out hover:scale-105"
            >
              <Trash2 class="w-5 text-red-600" />
              <span class="text-sm">Delete Task</span>
            </div>
          </DropdownMenuContent>
        </DropdownMenu>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-container {
  width: 340px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}

.grid-rows-layout {
  grid-template-rows: auto 1fr auto auto;
}

.ellipsis-icon {
  stroke-width: 3px;
}
</style>
