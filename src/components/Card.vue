<script setup lang="ts">
import {
  Circle,
  CalendarClock,
  Ellipsis,
  ListChecks,
  Trash2,
  Pencil,
} from "lucide-vue-next";

import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Separator } from "@/components/ui/separator";
import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuRadioGroup,
  DropdownMenuRadioItem,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";
import CategoryEdit from "./CategoryEdit.vue";
import { ref, watch } from "vue";

const props = defineProps({
  priorityColor: {
    type: String,
    required: true,
  },
  cardCategory: {
    type: String,
    required: true,
  },
  cardTitle: {
    type: String,
    required: true,
  },
  cardContent: {
    type: String,
    required: true,
  },
  cardDate: {
    type: String,
    required: true,
  },
});

const category = ref("");

const currentColor = ref(props.priorityColor);

const colors = [
  "text-green-500",
  "text-yellow-500",
  "text-orange-500",
  "text-red-500",
];

const handleColorChange = () => {
  const currentIndex = colors.indexOf(currentColor.value);
  const nextIndex = (currentIndex + 1) % colors.length;
  currentColor.value = colors[nextIndex];
};
</script>

<template>
  <div>
    <!-- FULL CARD -->
    <div class="card-container grid-rows-layout grid gap-3.5 rounded-lg p-5">
      <!-- HEADER OF CARD -->
      <div class="flex items-center justify-between">
        <div class="flex items-center gap-2">
          <Circle
            :class="`h-3 w-3 ${currentColor} cursor-pointer fill-current`"
            @click="handleColorChange"
          />
          <span class="font-medium">{{ cardCategory }}</span>
        </div>
        <!-- HEADER OF CARD - Category -->

        <DropdownMenu>
          <DropdownMenuTrigger as-child>
            <Button size="xs"><Pencil class="w-4" /></Button>
          </DropdownMenuTrigger>
          <DropdownMenuContent class="w-52">
            <DropdownMenuRadioGroup v-model="category">
              <DropdownMenuRadioItem value="No Categories found">
                No Categories found
              </DropdownMenuRadioItem>
              <CategoryEdit />
            </DropdownMenuRadioGroup>
          </DropdownMenuContent>
        </DropdownMenu>
      </div>

      <!-- BODY OF CARD -->
      <div class="-mt-1 flex flex-col gap-1">
        <Input
          type="text"
          :model-value="cardTitle"
          placeholder="Taskname..."
          class="h-7 resize-none truncate border-0 px-0 text-lg font-semibold focus-visible:ring-0 focus-visible:ring-offset-0"
        />

        <Textarea class="line-clamp-3 h-full resize-none text-sm outline-0">{{
          cardContent
        }}</Textarea>
      </div>

      <Separator class="w-full bg-gray-500" />

      <!-- FOOTER OF CARD -->
      <div class="flex items-center justify-between">
        <div class="flex items-center gap-2">
          <CalendarClock class="h-5 w-5" />
          <span class="text-sm">{{ cardDate }}</span>
        </div>

        <DropdownMenu>
          <DropdownMenuTrigger as-child>
            <Ellipsis
              class="h-6 w-6 cursor-pointer duration-300 ease-in-out hover:rotate-90"
            />
          </DropdownMenuTrigger>
          <DropdownMenuContent class="grid w-40">
            <div
              class="flex cursor-pointer items-center gap-2 rounded-lg px-3 py-0.5 duration-300 ease-in-out hover:bg-accent"
            >
              <ListChecks class="w-5 text-green-600" />
              <span class="text-sm">Task Done</span>
            </div>
            <div
              class="flex cursor-pointer items-center gap-2 rounded-lg px-3 py-0.5 duration-300 ease-in-out hover:bg-accent"
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
  height: 220px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}
.grid-rows-layout {
  grid-template-rows: auto 1fr auto auto;
}
.ellipsis-icon {
  stroke-width: 3px;
}
</style>
