<script setup lang="ts">
import { addDays, format } from 'date-fns'
import { ref } from 'vue'
import { CalendarIcon } from '@radix-icons/vue'

import { cn } from '@/lib/utils'
import { Button } from '@/components/ui/button'
import { Calendar } from '@/components/ui/calendar'
import {
  Popover,
  PopoverContent,
  PopoverTrigger,
} from '@/components/ui/popover'

const date = ref({
  start: new Date(2022, 0, 20),
  end: addDays(new Date(2022, 0, 20), 20),
})
</script>

<template>
  <div class="container mx-auto px-2">
    <div class="md:flex md:justify-between md:mb-8">
      <div class="mb-2 md:w-1/2 md:mr-4 p-4 bg-indigo-600">
        <h1>This is an about page</h1>
        <p class="mt-3">Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, cupiditate cumque aut quasi illum culpa impedit reiciendis dignissimos quam corporis earum sed, dolor esse ratione error excepturi numquam officiis beatae!
        Tenetur consequuntur quidem illum impedit obcaecati consectetur esse velit excepturi ratione laborum eveniet sapiente sunt voluptatibus reiciendis vitae non saepe aut quisquam, inventore maxime libero porro a exercitationem necessitatibus! Perferendis.</p>
      </div>
      <div class="mb-2 md:w-1/2 md:mr-4 p-4 bg-pink-900">
        <div :class="cn('grid gap-2', $attrs.class ?? '')">
    <Popover>
      <PopoverTrigger as-child>
        <Button
          id="date"
          :variant="'outline'"
          :class="cn(
            'w-[300px] justify-start text-left font-normal',
            !date && 'text-muted-foreground',
          )"
        >
          <CalendarIcon class="mr-2 h-4 w-4" />

          <span>
            {{ date.start ? (
              date.end ? `${format(date.start, 'LLL dd, y')} - ${format(date.end, 'LLL dd, y')}`
              : format(date.start, 'LLL dd, y')
            ) : 'Pick a date' }}
          </span>
        </Button>
      </PopoverTrigger>
      <PopoverContent class="w-auto p-0" align="start">
        <Calendar
          v-model.range="date"
          :columns="2"
        />
      </PopoverContent>
    </Popover>
  </div>
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
