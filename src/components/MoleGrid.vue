<template>
  <div class="grid text-center place-items-center">
    <h1 class="my-5 text-2xl">Whack A Mole</h1>
    <div v-if="start">
      <h2>Score: {{ score }}</h2>
      <h2>Time Left: {{ time }}</h2>
      <div v-if="time > 0" class="container"><div v-for="row in gridSize" :key="row">
        <span class="flex flex-row">
          <WhackAMole
            @mole-whack="handleWhack"
            v-for="col in gridSize"
            :key="col"
          ></WhackAMole>
        </span>
      </div></div>
      <div v-else>
        <h2>TIME IS UP!</h2>
      </div>
    </div>
    <div v-else>
        <button class="p-4 border-2 border-black" @click="startGame">Start</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import WhackAMole from "./WhackAMole.vue";
export default defineComponent({
  setup() {
    return {};
  },
  components: {
    WhackAMole,
  },
  data() {
    return {
      gridSize: 5 as number,
      score: 0 as number,
      time: 120,
      start: false,
      buzzer: new Audio(require('../assets/21871__nofeedbak__sarahbuzzer.mp3'))
    };
  },
  methods: {
    handleWhack() {
      this.score++;
    },
    startGame(){
        this.start = true;
        this.buzzer.play();
    }
  },
  mounted() {
    setInterval(() => {
      this.time--;
    }, 1000);
  },
});
</script>

<style scoped>
.container {
  /* cursor: url(http://www.rw-designer.com/cursor-extern.php?id=116484); */
  /* cursor: pointer; */
  cursor: url(../assets/icons8-thor-hammer-48.png), pointer;
}
</style>