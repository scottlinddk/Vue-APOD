<template>
<section class="text-gray-600 body-font">
  <div class="container mx-auto flex p-5 items-center justify-center flex-col">
    <img class="lg:w-2/6 md:w-3/6 w-5/6 mb-4 object-cover object-center rounded" :alt="apodDataObj.title" :src="apodDataObj.url">
    <div class="text-center lg:w-2/3 w-full">
      <h1 class="title-font sm:text-4xl text-3xl mb-2 font-medium text-gray-900">{{ apodDataObj.title }}</h1>
      <h2 class="title-font sm:text-xl text-l mb-4 font-medium text-gray-500">Copyright: {{ apodDataObj.copyright }}</h2>
      <AppModal :apod-data-obj="apodDataObj" class="mb-2"/>
      <p class="mb-8 leading-relaxed">{{ apodDataObj.explanation }}</p>
    </div>
  </div>
</section>
<!-- {{ apod.url }}
  <p>{{ apod }}</p> -->
</template>

<script>
import AppModal from './AppModal.vue'

export default {
  name: 'AppPhoto',
  components: {
    AppModal
  },
  props: {
    apodDataObj: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      apod: this.apodDataObj,
    }
  }
}
</script>

<style>

</style>