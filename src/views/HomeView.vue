<template>
  <main>
    <!-- <iframe height="1080" width="1080" src="https://editor.p5js.org/tleeaf/full/QcomVL4Dg"></iframe> -->
    <div class="mx-auto my-5">
      <div class="grid place-items-center"><button class="p-5 my-4 border-2 border-slate-800 w-100 btn" @click="LoadRandomSketch">Random Sketch</button></div>
      <RandomGradient v-if="activeIndex == 0"></RandomGradient>
      <SpinningShapes v-if="activeIndex == 1"></SpinningShapes>
      <PhotoPuzzle v-if="activeIndex == 2"></PhotoPuzzle>
      <Cipher v-if="activeIndex == 3"></Cipher>
      <MoneyLine v-if="activeIndex == 4"></MoneyLine>
      <Synthwave v-if="activeIndex == 5"></Synthwave>
      <MoleGrid v-if="activeIndex == 6"></MoleGrid>
      <!-- <Morse></Morse> -->
      <!-- <div class="grid grid-cols-3 grid-rows-4 gap-16 m-36">
            <div class="flex items-center justify-center flex-auto w-24 h-24 text-center border-2 border-black rounded-full animate-bounce hover:border-cyan-100">T</div>
            <div class="flex items-center justify-center flex-auto w-24 h-24 text-center border-2 border-black rounded-full animate-bounce hover:border-cyan-100">O</div>
            <div class="flex items-center justify-center flex-auto w-24 h-24 text-center border-2 border-black rounded-full animate-bounce hover:border-cyan-100">M</div>
            <div class="flex items-center justify-center flex-auto w-24 h-24 text-center border-2 border-black rounded-full animate-bounce hover:border-cyan-100">L</div>
            <div class="flex items-center justify-center flex-auto w-24 h-24 text-center border-2 border-black rounded-full animate-bounce hover:border-cyan-100">E</div>
            <div class="flex items-center justify-center flex-auto w-24 h-24 text-center border-2 border-black rounded-full animate-bounce hover:border-cyan-100">E</div>
        </div> -->

        <!-- Named Color Palette -->
        <!-- <ul class="grid grid-cols-6"><li v-for="c in colors" :ref="'color_'+c" class="grid h-32 font-bold place-content-center" :key="c" :style="'background:'+ `${c.toLowerCase()}`">{{c}}</li></ul> -->
        
    </div>
  </main>
</template>

<script lang="ts">
import RandomGradient from '@/components/RandomGradient.vue';
import SpinningShapes from '../components/SpinningShapes.vue';
import PhotoPuzzle from '../components/PhotoPuzzle.vue';
import { defineComponent } from '@vue/runtime-core';
import Cipher from '../components/Cipher.vue';
import MoneyLine from '../components/MoneyLine.vue';
import Morse from '../components/Morse.vue';
import Synthwave from '../components/Synthwave.vue';
import MoleGrid from '../components/MoleGrid.vue';

export default defineComponent({
  components: { RandomGradient, SpinningShapes, PhotoPuzzle, Cipher, MoneyLine, Morse, Synthwave, MoleGrid },
  data() {
    return {
      colors: [
        "AliceBlue",
        "AntiqueWhite",
        "Aqua",
        "Aquamarine",
        "Azure",
        "Beige",
        "Bisque",
        "Black",
        "BlanchedAlmond",
        "Blue",
        "BlueViolet",
        "Brown",
        "BurlyWood",
        "CadetBlue",
        "Chartreuse",
        "Chocolate",
        "Coral",
        "CornflowerBlue",
        "Cornsilk",
        "Crimson",
        "Cyan",
        "DarkBlue",
        "DarkCyan",
        "DarkGoldenRod",
        "DarkGray",
        "DarkGrey",
        "DarkGreen",
        "DarkKhaki",
        "DarkMagenta",
        "DarkOliveGreen",
        "DarkOrange",
        "DarkOrchid",
        "DarkRed",
        "DarkSalmon",
        "DarkSeaGreen",
        "DarkSlateBlue",
        "DarkSlateGray",
        "DarkSlateGrey",
        "DarkTurquoise",
        "DarkViolet",
        "DeepPink",
        "DeepSkyBlue",
        "DimGray",
        "DimGrey",
        "DodgerBlue",
        "FireBrick",
        "FloralWhite",
        "ForestGreen",
        "Fuchsia",
        "Gainsboro",
        "GhostWhite",
        "Gold",
        "GoldenRod",
        "Gray",
        "Grey",
        "Green",
        "GreenYellow",
        "HoneyDew",
        "HotPink",
        "IndianRed",
        "Indigo",
        "Ivory",
        "Khaki",
        "Lavender",
        "LavenderBlush",
        "LawnGreen",
        "LemonChiffon",
        "LightBlue",
        "LightCoral",
        "LightCyan",
        "LightGoldenRodYellow",
        "LightGray",
        "LightGrey",
        "LightGreen",
        "LightPink",
        "LightSalmon",
        "LightSeaGreen",
        "LightSkyBlue",
        "LightSlateGray",
        "LightSlateGrey",
        "LightSteelBlue",
        "LightYellow",
        "Lime",
        "LimeGreen",
        "Linen",
        "Magenta",
        "Maroon",
        "MediumAquaMarine",
        "MediumBlue",
        "MediumOrchid",
        "MediumPurple",
        "MediumSeaGreen",
        "MediumSlateBlue",
        "MediumSpringGreen",
        "MediumTurquoise",
        "MediumVioletRed",
        "MidnightBlue",
        "MintCream",
        "MistyRose",
        "Moccasin",
        "NavajoWhite",
        "Navy",
        "OldLace",
        "Olive",
        "OliveDrab",
        "Orange",
        "OrangeRed",
        "Orchid",
        "PaleGoldenRod",
        "PaleGreen",
        "PaleTurquoise",
        "PaleVioletRed",
        "PapayaWhip",
        "PeachPuff",
        "Peru",
        "Pink",
        "Plum",
        "PowderBlue",
        "Purple",
        "RebeccaPurple",
        "Red",
        "RosyBrown",
        "RoyalBlue",
        "SaddleBrown",
        "Salmon",
        "SandyBrown",
        "SeaGreen",
        "SeaShell",
        "Sienna",
        "Silver",
        "SkyBlue",
        "SlateBlue",
        "SlateGray",
        "SlateGrey",
        "Snow",
        "SpringGreen",
        "SteelBlue",
        "Tan",
        "Teal",
        "Thistle",
        "Tomato",
        "Turquoise",
        "Violet",
        "Wheat",
        "White",
        "WhiteSmoke",
        "Yellow",
        "YellowGreen",
      ],
      activeIndex: -1,
    };
  },
  methods: {
    LoadRandomSketch() {
      this.activeIndex = (this.activeIndex + 1)%7
    }
  },
  computed: {

  },
});
</script>


<style>
main{
  width: calc(100vw - 100px)
}
.btn:hover{
  background: linear-gradient(red,yellow,blue,magenta, );
}
</style>