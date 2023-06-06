<template>
  <div>
    <p>Your reaction time <u>{{ score }} ms </u></p>

    <p>You are {{ rank }}</p>
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  props: ['score']
  ,
  data() {
    return {
      rank: null as string | null
    }
  },
  mounted(): void {
    if (this.score < 250) {
      this.rank = "Godlike"
    } else if (this.score < 500) {
      this.rank = "a Pro"
    } else {
      this.rank = "too slow"
    }
  }
})
</script>

<style scoped>

div {
  font-size: 1.1rem;
  font-weight: bold;
  color: crimson;
  margin-top: 30px;
  text-align: center;
}

div p:nth-child(2) {
  font-size: 1.5rem;
  color: black;
  font-weight: bold;
}


</style>