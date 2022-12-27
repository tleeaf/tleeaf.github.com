<template>
  <div class="grid place-items-center" @keyup="something" ref="root">
    <h2 class="my-5 text-xl font-bold">Morse Code</h2>
    
    <div class="flex border-2 border-blue-300 rounded h-72">
      <span @mouseenter="onHover" class="grid h-full bg-gray-200 w-72 point text-9xl place-content-center hover:bg-gray-100">•</span>
      <span class="w-1/5 bg-slate-400"></span>
      <span @mouseenter="onHoverLong" class="grid h-full bg-gray-200 w-72 text-9xl place-content-center hover:bg-gray-100 ">-</span>
    </div>

  </div>
</template>

<script lang="ts">
import { ref, onMounted, defineComponent } from 'vue'
import * as Tone from 'tone';

const synth = new Tone.PolySynth().toDestination();

export default defineComponent({
  setup() {
      const root = ref(null)

      onMounted(() => {
        // the DOM element will be assigned to the ref after initial render
        console.log(root.value) // <div>This is a root element</div>
      })

      return {
        root
      }
    },
    data() {
        return {
            msg: ""
        }
    },
    mounted () {
      (this.$refs.container as any).focus();
    },
  methods: {
    onHover(){
      synth.triggerAttackRelease("C5", 0.05);
    },
    onHoverLong(){
      synth.triggerAttackRelease("C5","8n");
    },
    something(){
      alert("hi")
    }
  },
});
</script>

<style scoped>
</style>