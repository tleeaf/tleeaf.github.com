<template>
  <div class="grid place-items-center">
    <h1 class="text-xl font-bold">Money Line Betting Calculator</h1>
    <div class="flex flex-col"><span class="my-5 text-lg font-bold"><label for="odds" class="float-left ">Odds: ($)</label>
    <input
      type="number"
      name="odds"
      v-model="odds"
      class="border-2 border-gray-300 rounded"
      :class="odds > 0 ? 'text-green-500' : 'text-red-500'"
    /> <button @click="odds *= -1" class="px-3 border-2 border-gray-500 rounded-xl">Flip</button></span>
    <span class="relative flex my-5 text-lg font-bold"><label for="wager" class="">Wager: ($) </label>
    <input
      type="number"
      name="wager"
      step="100"
      v-model="wager"
      class="border-2 border-gray-300 rounded"
    /></span>
    <!-- <h3>Break Even: </h3>
        <h3>{{breakEven}}</h3> -->

    <span class="flex text-lg font-bold">
      <h3>Profit: $</h3>
      <h3>{{ betProfit.toFixed(2) }}</h3></span
    >
    <span class="flex text-lg font-bold">
      <h3>Return: $</h3>
      <h3>{{ betReturn.toFixed(2) }}</h3></span
    ></div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      wager: 100 as number,
      odds: 100 as number,
    };
  },
  computed: {
    breakEven(): number {
      return this.odds;
    },
    betProfit(): number {
      if (this.odds < 0) return (this.wager / -this.odds) * 100;
      else return (this.wager / 100) * this.odds;
    },
    betReturn(): number {
      return this.betProfit + this.wager;
    },
  },
});
</script>

<style scoped>
</style>