<template>
  <div>
    <button class="bg-blue-500 text-white active:bg-blue-600 uppercase text-sm px-4 py-2 rounded shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150" 
    type="button" @click="toggleModal()">
      View high resolution image
    </button>
    <div v-if="showModal" class="h-screen p-5 overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex">
      <div class="relative top-0 max-w-2xl mx-auto">
        <div class="border-0 rounded-lg shadow-lg relative flex flex-col w-full bg-white outline-none focus:outline-none">
          <!--header-->
          <div class="flex items-start justify-between p-3 border-b border-solid border-gray-200 rounded-t">
            <button class="p-1 ml-auto bg-transparent border-0 text-red opacity-5 float-right text-3xl leading-none font-bold outline-none focus:outline-none" v-on:click="toggleModal()">
              <span class="text-red text-3xl block outline-red focus:outline-red">
                Close
              </span>
            </button>
          </div>
          <!--body-->
          <div class="relative p-6 flex-auto">
            <img :alt="apodDataObj.title" :src="apodDataObj.hdurl">
          </div>
        </div>
      </div>
    </div>
    <div v-if="showModal" class="opacity-25 fixed inset-0 z-40 bg-black"></div>
  </div>
</template>

<script>
export default {
  name: "AppModal",
  props: {
    apodDataObj: {
      type: Object,
    }
  },
  data() {
    return {
        showModal: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    }
  }
}
</script>

<style>
span {
    color: black;
}
</style>