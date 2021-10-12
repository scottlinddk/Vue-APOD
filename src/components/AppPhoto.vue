<template>
<section class="text-gray-600 body-font">
  <div class="container mx-auto flex px-5 py-24 items-center justify-center flex-col">
    <img class="lg:w-2/6 md:w-3/6 w-5/6 mb-10 object-cover object-center rounded" alt="hero" :src="apod.url">
    <div class="text-center lg:w-2/3 w-full">
      <h1 class="title-font sm:text-4xl text-3xl mb-2 font-medium text-gray-900">{{ apod.title }}</h1>
      <h2 class="title-font sm:text-xl text-l mb-4 font-medium text-gray-500">{{ apod.copyright }}</h2>
      <p class="mb-8 leading-relaxed">{{ apod.explanation }}</p>
      <!-- <div class="flex justify-center">
        <button class="inline-flex text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg">Button</button>
        <button class="ml-4 inline-flex text-gray-700 bg-gray-100 border-0 py-2 px-6 focus:outline-none hover:bg-gray-200 rounded text-lg">Button</button>
      </div> -->
    </div>
  </div>
</section>
{{ apod.url }}
  <p>{{ apod }}</p>
</template>

<script>
export default {
  name: 'AppPhoto',
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