<template>
  <h1>Reaction Timer</h1>
  <button class="startButton" :class="{'buttonActive': isPlaying}" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @timerEnd="endTheGame"/>
  <Result v-if="showResult" :score="score"/>
</template>

<script lang="ts">

import {defineComponent} from "vue";
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default defineComponent({
  name: 'App',
  components: {
    Result,
    Block
  },
  data(): object {
    return {
      isPlaying: false as boolean,
      delay: null as number | null,
      score: null as number | null,
      showResult: false as boolean
    }
  },
  methods: {
    start(): void {
      this.delay = 2000 + Math.random() * 3000;
      this.isPlaying = !this.isPlaying;
      this.showResult = false;
    },
    endTheGame(reactionTime: number): void {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    }
  }
})

</script>


<style>
#root {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Montserrat', sans-serif;
  display: grid;

  place-items: center;
}

.startButton {
  padding: 10px 20px;
  border-radius: 10px;
  border: none;
  background-color: grey;
  color: white;
  font-size: 1.2rem;
  cursor: pointer;
}

.buttonActive {
  background-color: lightgray;
}


</style>
