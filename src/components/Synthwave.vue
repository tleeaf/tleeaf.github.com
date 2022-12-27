<template>
    <div class="w-full">
       <div class="mx-auto"> <h1 class="text-lg ">Synthwave Generator</h1>
        <button @click="playBassline" class="p-4 mx-2 border-2 border-black rounded hover:bg-teal-200">Play</button>
        <button @click="stop" class="p-4 mx-2 border-2 border-black rounded hover:bg-teal-200">Stop</button></div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import * as Tone from 'tone';

const synth = new Tone.PolySynth().toDestination();

const drum = new Tone.MembraneSynth().toDestination();
const snare = new Tone.NoiseSynth().toDestination();

const loopA = new Tone.Loop(time => {
	synth.triggerAttackRelease("C2", "8n", time);
    // drum.triggerAttackRelease("C2","4n", time);
}, "8n").start(0);
const loopB = new Tone.Loop(time => {
	// synth.triggerAttackRelease("C3", "8n", time);
    drum.triggerAttackRelease("C2","4n", time,0.5);
}, "4n").start(0);


export default defineComponent({
    setup () {
        

        return {}
    },
    methods: {
        playTone() {
            synth.triggerAttackRelease("C3", 0.05);
        },
        playBassline(){
            Tone.start();
            Tone.Transport.start();
        },
        stop(){
            Tone.Transport.stop();
        }
    },
})
</script>

<style scoped>

</style>