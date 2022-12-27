<template>
  <div class="grid place-items-center">
    <div class="grid mx-auto my-5 place-items-center">
      <h2 class="my-5 text-xl font-bold">Photo Puzzle using object-position</h2>
      <div class="flex my-5" v-if="!playing">
        <label for="subdivision" class="inline">Puzzle Resolution</label
        ><input
          name="subdivision"
          v-model="gridSize"
          type="number"
          class="inline ml-4 border-2 border-grey-50"
        />
        <button
        class="p-2 border-2 border-black hover:border-teal-300 "
        @click="jumbleTiles"
      >
        Start Puzzle
      </button>
      </div>
     

      <div v-show="winStatus"><h3>Puzzle Complete!! Nice Job!!</h3>
      <button @click="reset" title="another one!" class="block mx-auto border-2 rounded hover:border-teal-300 border-black-100"><img class="h-16" src="../assets/dj-khaled.png"/></button>
      </div>
    </div>
    <div>
      <div class="flex" v-for="j in gridSize" :key="j">
        <span class="flex m-0">
          <span v-for="i in gridSize" :key="i" draggable="true" class="dragtile"
            ><img
              @click="moveTile(i - 1 + (j - 1) * gridSize)"
              :src="'https://picsum.photos/800/800?random&dummyParam=' + dummyParam"
              class="m-0 img"
              :style="`${!playing ? 'border: 1px #CCC solid ' : ''} ${
                i - 1 + (j - 1) * gridSize == active
                  ? 'border: 3px hotpink solid'
                  : ''
              } ;width: ${800 / gridSize}px; height: ${
                800 / gridSize
              }px;object-position: -${
                ((tilePositions[(j - 1) * gridSize + (i - 1)] % gridSize) *
                  800) /
                gridSize
              }px -${
                (Math.floor(
                  tilePositions[(j - 1) * gridSize + (i - 1)] / gridSize
                ) *
                  800) /
                gridSize
              }px;`" /></span
        ></span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

function shuffleArray(array: number[]) {
  for (var i = array.length - 1; i > 0; i--) {
    var j = Math.floor(Math.random() * (i + 1));
    var temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  }
  return array;
}

export default defineComponent({
  name: "PhotoPuzzle",
  data() {
    return {
      gridSize: 3 as number,
      playing: false as boolean,
      active: -1 as number,
      tilePositions: Array.from(Array(3 ** 2).keys()) as number[],
      winStatus: false as boolean,
      dummyParam: 1 as number,
    };
  },
  methods: {
    moveTile(index: number): any {
      if (index !== this.active) {
        if (this.active == -1) {
          this.active = index;
          return;
        }
      } else {
        this.active = -1;
        return;
      }
      let temp = this.tilePositions[index];
      this.tilePositions[index] = this.tilePositions[this.active];
      this.tilePositions[this.active] = temp;
      this.active = -1;
      this.winStatus = this.puzzleInOrder;
    },
    jumbleTiles() {
      let arr = Array.from(Array(this.gridSize ** 2).keys());
      this.tilePositions = shuffleArray(shuffleArray(arr));
      this.playing = true;
    },
    reset(){
      this.winStatus = false;
      this.playing = false;
      this.dummyParam = Math.floor(Math.random()*10);
      this.$forceUpdate();
    }
  },
  computed: {
    puzzleInOrder(){
      for (var i = 0; i < this.tilePositions.length - 1; i++) {
        if (this.tilePositions[i] > this.tilePositions[i + 1]) return false;
      }
      return true;
    }
  },
  watch: {
    gridSize(value) {
      this.tilePositions = Array.from(Array(value ** 2).keys()) as number[];
    },
  },
  mounted() {
    // document.querySelector('.dragtile').addEventListener('handleDragStart', function() { this.style.opacity = '0.4' });
    // document.querySelector('.dragtile').addEventListener('handleDragEnd', function() { this.style.opacity = '1' });
    // let self = this;
    // window.addEventListener('keyup', function(ev) {
    //     self.moveTile(ev); // declared in your component methods
    // });
  },
});
</script>

<style lang="scss" scoped>
.img {
  //   clip-path: inset(0 90% 90% 0);
  //   margin: -90% 0;
  object-fit: none;
  cursor: move;
}
h3 {
  margin-top: 0px;
  margin-bottom: 10px;
  font-family: sans-serif;
  font-size: 6rem;
  background: linear-gradient(
    to right,
    #ef5350,
    #f48fb1,
    #7e57c2,
    #2196f3,
    #26c6da,
    #43a047,
    #eeff41,
    #f9a825,
    #ff5722
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>