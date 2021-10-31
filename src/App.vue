<template>
  <AppVideo v-if="dataReady && mediaType == 'video'" :apod-data-obj="apod" />
  <AppPhoto v-if="dataReady && mediaType == 'image'" :apod-data-obj="apod" />
  <!-- <AppDatepicker /> -->
  {{apod}}
  <div v-if="errors > 0" class="text-red">Something went wrong 😔 Try and reload the page.</div>
</template>
    <!-- 
      !! REMEMBER .ENV 😊
      1. Use fetch or AXIOS to fetch NASA API
      2. Check format 
      3. Check 'media type' from the API
      4. Render either Photo.vue or Video.vue depending on the media type
      5. Error handling
      6. Get yesterdays APOD (maybe) 
    
     -->
<script>
import axios from 'axios';

import AppVideo from './components/AppVideo.vue'
import AppPhoto from './components/AppPhoto.vue'
// import AppDatepicker from './components/AppDatepicker.vue'


export default {
  name: 'App',
  components: {
    AppVideo,
    AppPhoto,
    // AppDatepicker
  },
  data() {
    return {
      dataReady: false,
      apod: null,
      api: 'https://api.nasa.gov/planetary/apod?api_key=',
      key: process.env.VUE_APP_API_KEY,
      errors: [],
      mediaType: null,
    }
  },
  async created() {
    try {
      const response = await axios.get(this.api + this.key)
      this.apod = response.data
      this.mediaType = this.apod.media_type
      this.dataReady = true
    } catch (e) {
      this.errors.push(e)
    }
  },
  methods: {
    selectDate() {
      console.log(this.date)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 1em;
}

  .wrapper {
    max-width: 250px;
    margin: 0 auto;
  }
</style>
