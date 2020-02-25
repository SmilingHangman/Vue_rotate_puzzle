<template>
  <div>
    <input
      type="checkbox"
      id="checkbox"
      v-model="toggle"
      true-value="ON"
      false-value="OFF"
    >
    <label for="checkbox">Helper Borders {{ toggle }}</label>
  </div>
</template>

<script>
export default {
  name: 'HelperBorders',
  data () {
    return {
      toggle: 'OFF'
    }
  }
}
</script>

<style>

</style>
