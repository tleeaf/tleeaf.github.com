<template>
  <div class="grid place-items-center">
    <div class="grid mx-auto my-5 place-items-center">
        <h2 class="my-5 text-xl font-bold">Photo Puzzle using object-position</h2>
      <button v-if="!jumbledTiles" class="p-2 border-2 border-black" @click="jumbledTiles = true">
        Jumble Tiles
      </button>
    </div>
    <div>
      <div class="flex flex-col m-0" v-for="j in gridSize" :key="j">
        <span class="flex m-0">
          <img
            draggable="true"
            src="https://picsum.photos/800/800"
            v-for="i in gridSize"
            :key="i"
            class="m-0 img"
            :style="`width: ${800 / gridSize}px; height: ${
              800 / gridSize
            }px;object-position: -${
              ((tilePositions[(j - 1) * gridSize + (i - 1)] % gridSize) * 800) /
              gridSize
            }px -${
              (Math.floor(
                tilePositions[(j - 1) * gridSize + (i - 1)] / gridSize
              ) *
                800) /
              gridSize
            }px;`"
        /></span>
      </div>
    </div>
  </div>
</template>

<script>
function shuffleArray(array) {
  for (var i = array.length - 1; i > 0; i--) {
    var j = Math.floor(Math.random() * (i + 1));
    var temp = array[i];
    array[i] = array[j];
    array[j] = temp;
  }
  return array;
}

export default {
  name: "PhotoPuzzle",
  data() {
    return {
      gridSize: 11,
      jumbledTiles: false,
    };
  },
  methods: {},
  computed: {
    tilePositions() {
      let arr = Array.from(Array(this.gridSize ** 2).keys());
      if (this.jumbledTiles) return shuffleArray(arr);
      else return arr;
    },
  },
};
</script>

<style lang="scss" scoped>
.img {
  //   clip-path: inset(0 90% 90% 0);
  //   margin: -90% 0;
  object-fit: none;
  cursor: move;
}
</style>