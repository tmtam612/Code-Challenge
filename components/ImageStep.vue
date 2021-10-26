<template>
  <div>
    <div class="flex flex-row content-center justify-center mx-4 mt-4 h-10 rounded-lg">
      <div
        class="px-2 pt-1 border-l-2 border-t-2 border-b-2 border-light-blue-500 border-solid rounded-l-lg cursor-pointer"
        :class="selectedDefault === 1 ? 'bg-green-300 text-white' : 'text-green-600'"
        @click="switchImage(1)"
      >
        <span>Arbeitnehmer</span>
      </div>
      <div
        class="px-2 pt-1 border-2 border-light-blue-500 border-solid cursor-pointer"
        :class="selectedDefault === 2 ? 'bg-green-300 text-white' : 'text-green-600'"
        @click="switchImage(2)"
      >
        <span>Arbeitgeber</span>
      </div>
      <div
        class="px-2 pt-1 border-r-2 border-t-2 border-b-2 border-light-blue-500 border-solid rounded-r-lg cursor-pointer"
        :class="selectedDefault === 3 ? 'bg-green-300 text-white' : 'text-green-600'"
        @click="switchImage(3)"
      >
        <span>Temporärbüro</span>
      </div>
    </div>
    <img v-for="(url, index) in imageSource" :key="index" :src="url" class="w-full">
  </div>
</template>

<script>
export default {
  data () {
    return {
      selectedDefault: 1,
      arrImageName: {
        1: 'arbeitnehmer',
        2: 'arbeitgeber',
        3: 'temporarburo'
      },
      imageName: 'arbeitnehmer'
    }
  },
  computed: {
    imageSource () {
      return [
        require(`../assets/${this.imageName}_1.png`),
        require(`../assets/${this.imageName}_2.png`),
        require(`../assets/${this.imageName}_3.png`)
      ]
    }
  },
  methods: {
    switchImage (val) {
      this.selectedDefault = val
      this.imageName = this.arrImageName[val]
    }
  }
}
</script>
