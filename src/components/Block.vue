<template>
  <div class="block" :class="{'clicked': clicked }" v-if="showBlock" @click="stopTimer">
    <p v-if="!clicked">click me</p>
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  props: ['delay'],
  data() {
    return {
      showBlock: false as boolean,
      clicked: false as boolean,
      timer: null as any,
      reactionTime: 0 as number
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer);
      this.clicked = true;
      this.$emit("timerEnd", this.reactionTime)
    }
  }
})
</script>

<style scoped>

.block{
  color: white;
  height: 100px;
  width: 100px;
  background-color: crimson;

  border-radius: 10%;

  display: flex;
  justify-content: center;
  align-items: center;

  text-align: center;

  margin-top: 50px;

  cursor: pointer;

}
.clicked{
  background-color: green;
}

</style>

