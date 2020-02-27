<template>
  <div id="app">
    <PuzzleBox class="puzzle-box" :style="backgroundImage">
      <PuzzleCell></PuzzleCell>
    </PuzzleBox>
    <div
      v-for="(row, index) in grid"
      v-bind:key="index"
    >
      0
    </div>
    <div class="controls-wrapper">
      <BaseButton @click="fetchPicture">Get a Pic</BaseButton>
      <div class="controls-middle">
        <PuzzleSizeInput class="number-input"></PuzzleSizeInput>
        <HelperBorders></HelperBorders>
      </div>
      <BaseButton @click="StartGame">Start!</BaseButton>
    </div>
  </div>
</template>

<script>
import PuzzleBox from '@/components/PuzzleBox'
import BaseButton from '@/components/BaseButton'
import PuzzleSizeInput from '@/components/PuzzleSizeInput'
import HelperBorders from '@/components/HelperBorders'
import PuzzleCell from '@/components/PuzzleCell'

const axios = require('axios')
export default {
  name: 'App',
  components: {
    PuzzleBox,
    BaseButton,
    PuzzleSizeInput,
    HelperBorders,
    PuzzleCell
  },
  data () {
    return {
      isRequesting: false,
      picture: String,
      backgroundImage: '',
      grid: [],
      row: [],
      cell: '',
      size: 3
    }
  },
  methods: {
    async fetchPicture () {
      this.isRequesting = true
      try {
        const { data } = await axios.get(
          'https://api.thecatapi.com/v1/images/search?size=med',
          { headers: { 'x-api-key': 'b3c5b342-8b76-4f6a-bca6-14a7c4e6f0d9' } }
        )
        this.picture = data[0].url
        this.backgroundImage = 'background-image: url("' + this.picture + '"); background-color: #000000'
        this.isRequesting = false
      } catch (error) {
        this.isRequesting = false
      }
    },
    StartGame () {
      console.log('starting')
    }
  }
}
</script>

<style>
 .puzzle-box {
   background-repeat: no-repeat;
   background-size: 335px;
   background-position: left calc(50%);
   box-sizing: border-box;
 }

 .controls-wrapper {
   width: 335px;
   display: flex;
   justify-content: space-between;
   margin-top: 20px;
 }

 .controls-middle {
   width: 175px;
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
 }

 .number-input {
   max-width: 80px;
   text-align: center;
   padding: 4px 0;
 }
</style>
