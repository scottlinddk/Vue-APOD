<template>
<section class="text-gray-600 body-font">
  <div class="container mx-auto flex p-5 items-center justify-center flex-col">
    <!-- <img v-if="apodDataObj.thumbnail_url" class="lg:w-2/6 md:w-3/6 w-5/6 mb-4 object-cover object-center rounded" :alt="apodDataObj.title" :src="apodDataObj.thumbnail_url"> -->
    <div class="text-center lg:w-2/3 w-full mx-auto">
      <h1 class="title-font sm:text-4xl text-3xl mb-2 font-medium text-gray-900">{{ apodDataObj.title }}</h1>
      <h2 v-if="apodDataObj.copyright" class="title-font sm:text-xl text-l mb-4 font-medium text-gray-500">Copyright: {{ apodDataObj.copyright }}</h2>
      <AppVideoFrame :apod-data-obj="apodDataObj" class="mb-2 mx-auto"/>
      <p class="mb-8 leading-relaxed">{{ apodDataObj.explanation }}</p>
    </div>
  </div>
</section>
</template>

<script>
import AppVideoFrame from './AppVideoFrame.vue'

export default {
  name: "AppVideo",
  components: {
    AppVideoFrame
  },
  props: {
    apodDataObj: {
      type: Object,
    },
  },
  data() {
    return {
      // apod: this.apodDataObj,
    };
  },
};
</script>

<style>
</style>