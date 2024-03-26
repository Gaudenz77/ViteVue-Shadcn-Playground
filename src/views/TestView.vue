<script setup lang="ts">
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from '@/components/ui/card'
</script>

<template>
  <div class="container mx-auto">
    <!-- Top Row -->
    <div class="md:flex md:justify-between md:items-center md:mb-8">
      <div class="mb-2 md:w-1/2 md:mr-4">
        <!-- Content for the left column of the top row -->
        <div class="bgTest rounded p-4">
          Left Column Content
        </div>
      </div>
      <div class="mb-2 md:w-1/2 md:ml-4">
        <!-- Content for the right column of the top row -->
        <div class="bgTest rounded p-4">
          Right Column Content
        </div>
      </div>
    </div>
    <!-- Bottom Row -->
    <div class="md:flex md:justify-between">
      <div class="mb-2 md:w-1/3 md:mr-4">
        <!-- Content for the first column of the bottom row -->
        <div class="bgTest rounded p-4">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Voluptatum placeat repellat nobis magni iste neque cum eligendi autem fugiat vel iusto odio, quasi architecto consequuntur alias! Dolores praesentium tempora vitae.
          Nesciunt ipsum fugit necessitatibus nihil nobis eum unde maiores tempora quo? Voluptate consequatur fugit rerum sed ducimus labore exercitationem rem distinctio tenetur vero voluptatibus, laborum ipsum omnis aperiam optio aliquid?
        </div>
      </div>
      <div class="mb-2 md:w-1/3 md:mx-2">
        <!-- Content for the second column of the bottom row -->
        <div class="bgTest rounded p-4">
          <Card>
    <CardHeader>
      <CardTitle>Card Title</CardTitle>
      <CardDescription>Card Description</CardDescription>
    </CardHeader>
    <CardContent>
      Second Column Content
    </CardContent>
    <CardFooter>
      Card Footer
    </CardFooter>
  </Card>
          
        </div>
      </div>
      <div class="mb-2 md:w-1/3 md:ml-4">
        <!-- Content for the third column of the bottom row -->
        <div class="bgTest rounded p-4">
          Third Column Content
        </div>
      </div>
    </div>
  </div>
</template>
  
<style>
@media (min-width: 1024px) {
  .testpage {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>