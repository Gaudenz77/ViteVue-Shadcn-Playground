<script setup lang="ts">
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

// table

import {
  Table,
  TableBody,
  TableCaption,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from "@/components/ui/table";

const invoices = [
  {
    invoice: "INV001",
    paymentStatus: "Paid",
    totalAmount: "$250.00",
    paymentMethod: "Credit Card",
  },
  {
    invoice: "INV002",
    paymentStatus: "Pending",
    totalAmount: "$150.00",
    paymentMethod: "PayPal",
  },
  {
    invoice: "INV003",
    paymentStatus: "Unpaid",
    totalAmount: "$350.00",
    paymentMethod: "Bank Transfer",
  },
  {
    invoice: "INV004",
    paymentStatus: "Paid",
    totalAmount: "$450.00",
    paymentMethod: "Credit Card",
  },
  {
    invoice: "INV005",
    paymentStatus: "Paid",
    totalAmount: "$550.00",
    paymentMethod: "PayPal",
  },
  {
    invoice: "INV006",
    paymentStatus: "Pending",
    totalAmount: "$200.00",
    paymentMethod: "Bank Transfer",
  },
  {
    invoice: "INV007",
    paymentStatus: "Unpaid",
    totalAmount: "$300.00",
    paymentMethod: "Credit Card",
  },
];

import { ref } from "vue";
import {
  PinInput,
  PinInputGroup,
  PinInputInput,
  PinInputSeparator,
} from "@/components/ui/pin-input";

const value = ref<string[]>([]);
const handleComplete = (e: string[]) => alert(e.join(""));
</script>

<template>
  <div class="container mx-auto px-2">
    <!-- Top Row -->
    <div class="md:flex md:justify-between md:items-center md:mb-8">
      <div class="mb-2 md:w-1/2 md:mr-4">
        <!-- Content for the left column of the top row -->
        <div class="bgTest rounded p-4">Left Column Content</div>
      </div>
      <div class="mb-2 md:w-1/2 md:ml-4">
        <!-- Content for the right column of the top row -->
        <div class="bgTest rounded p-4">Right Column Content</div>
      </div>
    </div>
    <!-- Bottom Row -->
    <div class="md:flex md:justify-between">
      <div class="mb-2 md:w-1/3 md:mr-4">
      
        <!-- Content for the first column of the bottom row -->
        <div class="bgTest rounded p-4">
          
          <div class="pinOwn flex flex-wrap justify-center ">
            <PinInput
              id="pin-input"
              v-model="value"
              placeholder="○"
              @complete="handleComplete"
            >
              <PinInputGroup class="gap-1">
                <template v-for="(id, index) in 5" :key="id">
                  <PinInputInput class="pinText rounded-md border " :index="index" />
                  <template v-if="index !== 4">
                    <!-- <PinInputSeparator /> -->
                  </template>
                </template>
              </PinInputGroup>
            </PinInput>
      
        </div>
         
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
            <CardContent> Second Column Content </CardContent>
            <CardFooter> Card Footer </CardFooter>
          </Card>
        </div>
      </div>
      <div class="mb-2 md:w-1/3 md:ml-4">
        <!-- Content for the third column of the bottom row -->
        <div class="bgTest rounded p-4">
          <Table>
            <TableCaption>A list of your recent invoices.</TableCaption>
            <TableHeader>
              <TableRow>
                <TableHead class="w-[100px]"> Invoice </TableHead>
                <TableHead>Status</TableHead>
                <TableHead>Method</TableHead>
                <TableHead class="text-right"> Amount </TableHead>
              </TableRow>
            </TableHeader>
            <TableBody>
              <TableRow v-for="invoice in invoices" :key="invoice.invoice">
                <TableCell class="font-medium">
                  {{ invoice.invoice }}
                </TableCell>
                <TableCell>{{ invoice.paymentStatus }}</TableCell>
                <TableCell>{{ invoice.paymentMethod }}</TableCell>
                <TableCell class="text-right">
                  {{ invoice.totalAmount }}
                </TableCell>
              </TableRow>
            </TableBody>
          </Table>
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
