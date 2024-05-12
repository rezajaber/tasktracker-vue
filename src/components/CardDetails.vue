<script setup lang="ts">
import { Layers } from "lucide-vue-next";
import { GalleryVerticalEnd } from "lucide-vue-next";
import { Calendar as CalendarIcon } from "lucide-vue-next";

import { ref } from "vue";

import { Button } from "@/components/ui/button";
import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuRadioGroup,
  DropdownMenuRadioItem,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";

import {
  DateFormatter,
  type DateValue,
  getLocalTimeZone,
} from "@internationalized/date";

import { Calendar } from "@/components/ui/calendar";
import {
  Popover,
  PopoverContent,
  PopoverTrigger,
} from "@/components/ui/popover";
import { cn } from "@/lib/utils";
import MarkDownLegend from "./MarkDownLegend.vue";

const df = new DateFormatter("en-US", {
  dateStyle: "long",
});

const value = ref<DateValue>();

const priority = ref("priority");
const category = ref("category");
</script>

<template>
  <div>
    <div class="flex justify-between">
      <div class="flex gap-2">
        <!-- PRIORITY -->
        <DropdownMenu>
          <DropdownMenuTrigger as-child>
            <Button><GalleryVerticalEnd class="mr-1.5 w-4" />Priority</Button>
          </DropdownMenuTrigger>
          <DropdownMenuContent class="w-40">
            <DropdownMenuRadioGroup v-model="priority">
              <DropdownMenuRadioItem value="Critical">
                Critical
              </DropdownMenuRadioItem>
              <DropdownMenuRadioItem value="High"> High </DropdownMenuRadioItem>
              <DropdownMenuRadioItem value="Normal">
                Normal
              </DropdownMenuRadioItem>
              <DropdownMenuRadioItem value="Low"> Low </DropdownMenuRadioItem>
            </DropdownMenuRadioGroup>
          </DropdownMenuContent>
        </DropdownMenu>

        <!-- CATEGORY -->
        <DropdownMenu>
          <DropdownMenuTrigger as-child>
            <Button><Layers class="mr-1.5 w-4" />Category</Button>
          </DropdownMenuTrigger>
          <DropdownMenuContent class="w-52">
            <DropdownMenuRadioGroup v-model="category">
              <DropdownMenuRadioItem value="Critical">
                No Categories found
              </DropdownMenuRadioItem>
            </DropdownMenuRadioGroup>
          </DropdownMenuContent>
        </DropdownMenu>
      </div>

      <div class="flex gap-2">
        <!-- CALENDER -->
        <Popover>
          <PopoverTrigger as-child>
            <Button
              :class="
                cn('w-fit justify-start bg-primary', !value && 'text-white')
              "
            >
              <CalendarIcon class="mr-1.5 w-4 text-white" />
              {{
                value
                  ? df.format(value.toDate(getLocalTimeZone()))
                  : "Pick a date"
              }}
            </Button>
          </PopoverTrigger>
          <PopoverContent class="w-auto p-0">
            <Calendar v-model="value" initial-focus />
          </PopoverContent>
        </Popover>

        <MarkDownLegend />
      </div>
    </div>
  </div>
</template>
