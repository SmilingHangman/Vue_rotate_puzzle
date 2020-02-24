<template>
  <div id="app">
    <PuzzleBox></PuzzleBox>
    <BaseButton>Get a Pic</BaseButton>
  </div>
</template>

<script>
import PuzzleBox from '@/components/PuzzleBox'
import BaseButton from '@/components/BaseButton'
export default {
  name: 'App',
  components: {
    PuzzleBox,
    BaseButton
  }
}
</script>

<style>
</style>
