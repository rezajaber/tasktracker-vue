<script setup lang="ts">
import { ref } from "vue";

import { Search } from "lucide-vue-next";
import { CirclePlus } from "lucide-vue-next";
import { SlidersHorizontal } from "lucide-vue-next";

import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import type { DropdownMenuCheckboxItemProps } from "radix-vue";

import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuGroup,
  DropdownMenuCheckboxItem,
  DropdownMenuLabel,
  DropdownMenuSeparator,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";

type Checked = DropdownMenuCheckboxItemProps["checked"];

const showDone = ref<Checked>(false);
const overdue = ref<Checked>(false);
const critical = ref<Checked>(false);
const high = ref<Checked>(false);
const normal = ref<Checked>(false);
const low = ref<Checked>(false);
</script>

<template>
  <div class="mx-auto grid justify-between gap-2 md:mx-0 md:flex">
    <div class="flex gap-2">
      <div class="relative w-[22rem] max-w-md items-center md:w-96">
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

      <Button class="hidden md:flex" type="submit"
        ><CirclePlus class="mr-1.5 w-4" />Create Task</Button
      >
    </div>

    <div class="flex justify-between">
      <Button class="md:hidden" type="submit"
        ><CirclePlus class="mr-1.5 w-4" />Create Task</Button
      >

      <DropdownMenu>
        <DropdownMenuTrigger as-child>
          <Button><SlidersHorizontal class="mr-1.5 w-4" />Filter</Button>
        </DropdownMenuTrigger>
        <DropdownMenuContent class="w-56">
          <DropdownMenuLabel>Status</DropdownMenuLabel>
          <DropdownMenuSeparator />
          <DropdownMenuGroup>
            <DropdownMenuCheckboxItem v-model:checked="showDone">
              Show Done
            </DropdownMenuCheckboxItem>
            <DropdownMenuCheckboxItem v-model:checked="overdue">
              Overdue
            </DropdownMenuCheckboxItem>
            <DropdownMenuSeparator />
          </DropdownMenuGroup>
          <DropdownMenuLabel>Priorities</DropdownMenuLabel>
          <DropdownMenuSeparator />
          <DropdownMenuCheckboxItem v-model:checked="critical">
            Critical
          </DropdownMenuCheckboxItem>
          <DropdownMenuCheckboxItem v-model:checked="high">
            High
          </DropdownMenuCheckboxItem>
          <DropdownMenuCheckboxItem v-model:checked="normal">
            Normal
          </DropdownMenuCheckboxItem>
          <DropdownMenuCheckboxItem v-model:checked="low">
            Low
          </DropdownMenuCheckboxItem>
        </DropdownMenuContent>
      </DropdownMenu>
    </div>
  </div>
</template>
