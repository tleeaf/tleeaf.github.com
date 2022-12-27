<template>
  <div class="w-24 h-24 border-2 border-black">
    <div
      v-if="popped"
      @click="whack"
      class="absolute bottom-0 w-full bg-yellow-900 rounded rounded-t-full h-5/6"
    >
      <span
        class="absolute w-4 h-4 bg-red-400 rounded-full top-10 left-10"
      ></span>
      <span class="absolute w-4 h-4 bg-white rounded-full top-5 left-5">
        <span class="absolute w-2 h-2 bg-black rounded-full top-1 left-1"></span
      ></span>
      <span class="absolute w-4 h-4 bg-white rounded-full top-5 right-5"
        ><span
          class="absolute w-2 h-2 bg-black rounded-full top-1 left-1"
        ></span
      ></span>
      <span class="absolute h-1 border-2 border-black left-7 w-9 bottom-2"></span>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
declare var require: any
export default defineComponent({
  setup() {
    return {};
  },
  name: "WhackAMole",
  data() {
    return {
      gridSize: 5 as number,
      timeUp: 5 as number,
      popped: false as boolean,
      hit: false as boolean,
    //   sound: new Audio(require('../assets/244657__greenvwbeetle__pop-5.flac'))
    };
  },
  methods: {
    whack() {
      this.popped = false;
      this.hit = true;
      this.$emit('moleWhack');
    },
    setPop() {
      setTimeout(() => {
        this.popped = true;
        // this.sound.play();
        setTimeout(() => {
          this.popped = false;
          this.setPop();
        }, 3000 * Math.random() + 500);
      }, 1000 * Math.random() * 40);
    },
  },
  mounted() {
    this.setPop();
  },
});
</script>

<style scoped>
</style>