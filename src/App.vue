<template>
  <AppVideo v-if="dataReady && mediaType == 'video'" :apod-data-obj="apod" />
  <AppPhoto v-if="dataReady && mediaType == 'image'" :apod-data-obj="apod" />
  <!-- <DatePicker v-if="selectDate(date)" v-model="date" mode="date" :model-config="modelConfig" :available-dates='{ start: new Date(1995, 6, 16), end: null }'/> -->
      <DatePicker
      v-if="selectDate(date)"
      v-model="date"
      mode="date"
      :model-config="modelConfig"
      :available-dates="{ start: new Date(1995, 6, 16), end: null }"
    />
  {{apod}}
  <div v-if="errors > 0" class="text-red">Something went wrong 😔 Try and reload the page.</div>
</template>
<script>
import axios from 'axios';

import AppVideo from './components/AppVideo.vue'
import AppPhoto from './components/AppPhoto.vue'
// import AppDatePicker from './components/AppDatePicker.vue'
// import AppDatePicker from './components/AppDatePicker.vue';
import { DatePicker } from 'v-calendar';


export default {
  name: 'App',
  components: {
    AppVideo,
    AppPhoto,
    // AppDatePicker,
    DatePicker
  },
  data() {
    return {
      dataReady: false,
      apod: null,
      api: 'https://api.nasa.gov/planetary/apod?api_key=',
      key: process.env.VUE_APP_API_KEY,
      errors: [],
      mediaType: null,
      showDatePicker: false,
      date: new Date(),
      selectedDate: null,
      modelConfig: {
        type: 'string',
        mask: 'YYYY-MM-DD', // Uses 'iso' if missing
      },
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
    async selectDate() {
        const response = await axios.get(this.api + this.key + '&date=' + this.date)
        this.apod = await response.data
        this.mediaType = this.apod.media_type
        this.dataReady = true
    },
    togglePicker() {
      this.showDatePicker = !this.showDatePicker;
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
