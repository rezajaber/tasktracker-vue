<script setup lang="ts">
import { Button } from "@/components/ui/button";
import { CirclePlus, Trash2 } from "lucide-vue-next";

import Input from "./ui/input/Input.vue";
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
  DialogFooter,
} from "@/components/ui/dialog";
</script>

<template>
  <div>
    <Dialog>
      <DialogTrigger as-child>
        <Button class="my-1 w-full"
          ><CirclePlus class="mr-1.5 w-4" />Edit Categories</Button
        >
      </DialogTrigger>

      <DialogContent class="sm:max-w-[425px]">
        <DialogHeader>
          <DialogTitle>Edit Categories</DialogTitle>
          <DialogDescription
            >Here you can add or delete categories!
          </DialogDescription>
        </DialogHeader>

        <div class="grid gap-5">
          <div class="grid gap-2">
            <div class="flex gap-2">
              <Input
                disabled
                class="border border-primary bg-primary text-white"
              />
              <Button><Trash2 class="w-5" /></Button>
            </div>
          </div>

          <div class="flex flex-col gap-2">
            <Input
              placeholder="Create a new Task..."
              class="border border-primary focus-visible:ring-0"
            />
            <Button type="submit">Create</Button>
          </div>
        </div>
      </DialogContent>
    </Dialog>
  </div>
</template>
