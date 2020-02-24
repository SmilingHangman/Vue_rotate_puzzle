<template>
  <button
    @click="onClick"
  >
    <slot />
  </button>
</template>

<script>
export default {
  name: 'BaseButton',
  methods: {
    onClick (event) {
      if (!this.disabled) {
        this.$emit('click', event)
      }
    }
  }
}
</script>

<style>
  button {
    font-family: 'Mansalva', cursive;
    font-size: 12px;
    width: 70px;
    height: 70px;
    border-radius: 50%;
    text-align: center;
    color: pink;
    background-color: rgb(99, 41, 85);
    border-top-color:  rgb(209, 147, 195);
    border-left-color: rgb(209, 147, 195);
    border-right-color: rgb(207, 163, 197);
    border-bottom-color: rgb(207, 163, 197);
  }
</style>
