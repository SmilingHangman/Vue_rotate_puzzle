<template>
  <div id="app">
    <PuzzleBox class="puzzle-box" :style="backgroundImage"></PuzzleBox>
    <BaseButton @click="fetchPicture">Get a Pic</BaseButton>
  </div>
</template>

<script>
import PuzzleBox from '@/components/PuzzleBox'
import BaseButton from '@/components/BaseButton'

const axios = require('axios')

export default {
  name: 'App',
  components: {
    PuzzleBox,
    BaseButton
  },
  data () {
    return {
      isRequesting: false,
      picture: String,
      backgroundImage: ''
    }
  },
  // created () {
  //   this.fetchPicture()
  // },
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
    }
  }
}
</script>

<style>
 .puzzle-box {
   background-repeat: no-repeat;
   background-size: 335px;
   background-position: left calc(50%);
 }
</style>
