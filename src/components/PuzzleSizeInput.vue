<template>
  <input
    v-model.number="setPuzzleSize"
    type="number"
    min="3"
    max="7"
  >
</template>

<script>
export default {
  name: 'PuzzleSizeInput',
  data () {
    return {
      setPuzzleSize: 3
    }
  },
  computed: {
    minMax () {
      if (this.setPuzzleSize < 3) {
        return this.setPuzzleSize === 3
      } if (this.setPuzzleSize > 7) {
        return this.setPuzzleSize === 7
      } else {
        return this.setPuzzleSize
      }
    }
  }
}
</script>

<style>

</style>
