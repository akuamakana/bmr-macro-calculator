<template>
  <div class="bg-gray-700 rounded-lg flex flex-col w-full p-6 shadow-lg">
    <h1 class="block text-3xl text-teal-200 font-bold mb-2">
      Exercise Level
    </h1>
    <div class="flex justify-between self-center h-full items-center w-full">
      <div class="flex justify-between items-center">
        <input
          v-model="level"
          type="radio"
          name="level"
          value="1.2"
          class="mr-3"
          @change="calcBMR"
        >
        <label for="0">Little/None</label>
      </div>
      <div class="flex justify-between items-center">
        <input
          v-model="level"
          type="radio"
          name="level"
          value="1.375"
          class="mr-3"
          @change="calcBMR"
        >
        <label for="0">Light</label>
      </div>
      <div class="flex justify-between items-center">
        <input
          v-model="level"
          type="radio"
          name="level"
          value="1.55"
          class="mr-3"
          @change="calcBMR"
        >
        <label for="0">Moderate</label>
      </div>
      <div class="flex justify-between items-center">
        <input
          v-model="level"
          type="radio"
          name="level"
          value="1.725"
          class="mr-3"
          @change="calcBMR"
        >
        <label for="0">Very Active</label>
      </div>
      <div class="flex justify-between items-center">
        <input
          v-model="level"
          type="radio"
          name="level"
          value="1.9"
          class="mr-3"
          @change="calcBMR"
        >
        <label for="0">Extra Active</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      level: 1.55
    }
  },
  methods: {
    calcBMR () {
      this.$emit('levelChange', this.level)
    }
  }
}
</script>
