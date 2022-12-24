<template>
  <div>
    <div class="grid place-items-center">
      <h2 class="my-5 text-xl font-bold">Random Spinning Shapes</h2>
      <button
        class="p-2 my-4 border-2 border-slate-800 w-100 hover:bg-pink-200"
        @click="RandomColors"
      >
        Random Colors
      </button>
    </div>
  </div>
  <div v-if="active" class="container relative animate-spin">
    <div
      v-for="i in 10"
      class="absolute item"
      :key="i"
      :style="`width: 20px; height: 20px; border-radius: ${Math.random() * 40}px;background: rgb(${
        minChannelVal + Math.random() * remainder
      },${minChannelVal + Math.random() * remainder},${
        minChannelVal + Math.random() * remainder
      });transform: translate(40vw,40vh) rotate(${
        (360 / 10) * i
      }deg) translate(${Math.sin(345)*i*50}px)`"
    ></div>
  </div>
</template>

<script lang="ts">
import  { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  name: "SpinningShapes",
  data() {
    return {
      minChannelVal: 0,
      active: true,
    };
  },
  methods: {
    RandomColors() {
      this.active = false;
      this.active = true;
    },
  },
  computed: {
    remainder(): number {
      return 255 - this.minChannelVal;
    },
  },
});
</script>

<style lang="scss" scoped>
.item {
  animation-duration: 1s;
//   animation-name: spin;
  animation-duration: 1000ms;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(10deg);
    }
  }
}
.container {
  pointer-events: none;
  animation-duration: 10s;

  height: calc(100vh - 100px);
}
</style>