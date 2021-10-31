<template>
  <div class="relative p-6 flex-auto">
    <DatePicker
      v-if="selectDate(date)"
      v-model="date"
      mode="date"
      :model-config="modelConfig"
      :available-dates="{ start: new Date(1995, 6, 16), end: null }"
    />
  </div>
</template>

<script>
import axios from 'axios';

import { DatePicker } from "v-calendar";

export default {
  name: "AppDatePicker",
  components: {
    DatePicker,
  },
  data() {
    return {
      selectedDate: null,
      modelConfig: {
        type: "string",
        mask: "YYYY-MM-DD", // Uses 'iso' if missing
      },
    };
  },
  methods: {
    async selectDate() {
      try {
        const response = await axios.get(this.api + this.key + '&date=' + this.date)
        this.apod = await response.data
        this.mediaType = this.apod.media_type
        this.dataReady = true
    } catch (e) {
        this.errors.push(e)
    }
    }
  }
}
</script>

<style>
</style>