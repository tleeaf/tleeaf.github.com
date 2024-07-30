<template>
  <div class="w-24 h-24 bg-green-600 border-2 border-black">
    <div
      v-if="popped || hit"
      @click="whack"
      class="absolute bottom-0 w-full overflow-hidden bg-yellow-900 rounded rounded-t-full h-2/3"
      :style="hit ? `height: 66%` : `height: 85%`"
    >
      <span
        class="absolute w-4 h-4 bg-red-400 rounded-full top-10 left-10"
      >  <span class="absolute right-0 w-1 h-1 bg-red-900 rounded-full bottom-1"></span> <span class="absolute left-0 w-1 h-1 bg-red-900 rounded-full bottom-1"></span></span>
      <!-- Left Eye -->
      <span class="absolute w-4 h-4 bg-white rounded-full top-5 left-5">
        <span
          v-if="!hit"
          class="absolute top-0 w-2 h-4 bg-black rounded-full left-1"
          ><span
            class="absolute top-0 left-0 w-1 h-1 bg-white rounded-full"
          ></span
        ></span>
        <span
          v-else
          class="absolute left-0 text-2xl font-black text-black"
          style="top: -10px"
          >X</span
        >
      </span>
      <!-- Right Eye -->
      <span class="absolute w-4 h-4 bg-white rounded-full top-5 right-5"
        ><span
          v-if="!hit"
          class="absolute top-0 w-2 h-4 bg-black rounded-full left-1"
        >
          <span
            class="absolute top-0 left-0 w-1 h-1 bg-white rounded-full"
          ></span
        ></span>
        <span
          v-else
          class="absolute left-0 text-2xl font-black text-black"
          style="top: -10px"
          >X</span
        >
      </span>
      <!-- Mouth -->
      <span
        v-if="!hit"
        class="absolute h-1 border-2 border-black left-7 w-9 bottom-2"
      ><span class="absolute w-2 h-4 bg-white border-r-2 border-black left-2"></span> <span class="absolute w-2 h-4 bg-white left-4"></span></span>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import pop from "../assets/376968__elmasmalo1__bubble-pop.wav";
import ow from "../assets/223486__mrgreaper__bunnyoww.ogg";
let popup: any;
export default defineComponent({
  setup() {
    return {};
  },
  name: "WhackAMole",
  props: {
    enabled: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      popped: false as boolean,
      hit: false as boolean,
      sound: new Audio(pop),
    };
  },
  methods: {
    disable() {
      clearTimeout(popup);
    },
    whack() {
      if (this.hit) return;
      this.hit = true;
      const owSFX = new Audio(ow);
      owSFX.play();
      this.$emit("moleWhack");
      setTimeout(() => {
        this.popped = false;
        this.hit = false;
      }, 1000);
    },
    setPop() {
      console.log("pop set");
      popup = setTimeout(() => {
        this.hit = false;
        this.popped = true;
        this.sound.play();

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
  watch: {
    enabled(newValue, oldValue) {
      if (!newValue && oldValue) this.disable();
    },
  },
});
</script>

<style scoped>
</style>