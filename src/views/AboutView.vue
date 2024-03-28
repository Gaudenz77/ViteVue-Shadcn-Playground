<script setup lang="ts">
import { addDays, format } from "date-fns";
import { ref } from "vue";
import { CalendarIcon } from "@radix-icons/vue";
import { cn } from "@/lib/utils";
import { Button } from "@/components/ui/button";
import { Calendar } from "@/components/ui/calendar";
import { Popover, PopoverContent, PopoverTrigger } from "@/components/ui/popover";
import { Label } from "@/components/ui/label";
import { Input } from "@/components/ui/input";

const date = ref({
  start: new Date(2022, 0, 20),
  end: addDays(new Date(2022, 0, 20), 20),
});

const title = ref('');
const tableData = ref([]);

const handleSubmit = () => {
  // Push the form data (title and date range) to the tableData array
  const formData = { title: title.value, date: `${format(date.value.start, 'LLL dd, y')} - ${format(date.value.end, 'LLL dd, y')}` };
  tableData.value.push(formData);

  // Store form data in sessionStorage
  sessionStorage.setItem('formData', JSON.stringify(formData));

  // Clear the form fields
  title.value = '';
  date.value = {
    start: null,
    end: null
  };
}

import { onMounted } from 'vue';

onMounted(() => {
  const storedData = sessionStorage.getItem('formData');
  if (storedData) {
    tableData.value = [JSON.parse(storedData)];
  }
});


import {
  Table,
  TableBody,
  TableCaption,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from '@/components/ui/table'
</script>

<template>
  <div class="container mx-auto px-2">
    <div class="md:flex md:justify-between md:mb-8">
      <div class="mb-2 md:w-1/2 md:mr-4 p-4 bg-indigo-600">
        <h1>This is an about page</h1>
        <form @submit.prevent="handleSubmit">
          <div class="formCal md:w-1/2 mb-3">
            <Label for="description">Title of Event</Label>
            <Input v-model="title" type="text" name="title" class="" />
          </div>
          <Label for="datePick">Date (from/to)</Label>
          <div class=" md:w-1/2 mb-3" :class="cn('grid gap-2', $attrs.class ?? '')">
            <Popover>
              <PopoverTrigger as-child>
                <Button
                  id="date"
                  :variant="'outline'"
                  :class="
                    cn(
                      'md:w-100 justify-start text-left font-normal',
                      !date && 'text-muted-foreground'
                    )
                  "
                >
                  <CalendarIcon class="hidden md:block mr-2 h-4 w-4" />
                  <span class="dateSpan">
                    {{
                      date.start
                        ? date.end
                          ? `${format(date.start, "LLL dd, y")} - ${format(
                              date.end,
                              "LLL dd, y"
                            )}`
                          : format(date.start, "LLL dd, y")
                        : "Pick a date"
                    }}
                  </span>
                </Button>
              </PopoverTrigger>
              <PopoverContent class="w-auto p-0" align="start">
                <Calendar v-model.range="date" :columns="2" />
              </PopoverContent>
            </Popover>
          </div>
          <div class="flex justify-center md:justify-start">
            <Button class="bg-emerald-500 mt-3" type="submit">Submit</Button>
          </div>
          
        </form>
      </div>

      <div class="mb-2 md:w-1/2 md:mr-4 p-4 bg-pink-900">
        <Table>
          <TableHeader class="tableTitle">
            <TableRow>
              <TableHead>Title</TableHead>
              <TableHead>Date Range</TableHead>
            </TableRow>
          </TableHeader>
          <TableBody>
            <TableRow v-for="(item, index) in tableData" :key="index">
              <TableCell>{{ item.title }}</TableCell>
              <TableCell>{{ item.date }}</TableCell>
            </TableRow>
          </TableBody>
        </Table>
      </div>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

