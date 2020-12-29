<template>
  <div class="bg-gray-700 rounded-lg flex flex-col p-6 shadow-lg">
    <div class="flex justify-between items-center ">
      <h1 class="block text-3xl text-teal-200 font-bold mb-2">
        Personal Stats
      </h1>
      <div class="flex">
        <p>Imperial</p>
        <div class="w-12 h-6 bg-gray-300 rounded-full flex-shrink-0 p-1 duration-300 ease-in-out mx-2" :class="{'bg-teal-200': stats.isMetric}" @click="stats.isMetric = !stats.isMetric">
          <div class="bg-white w-4 h-4 rounded-full shadow-md transform duration-300 ease-in-out" :class="{'translate-x-6': stats.isMetric}" />
        </div>
        <p>Metric</p>
      </div>
    </div>
    <div class="flex items-center">
      <div class="grid grid-flow-col auto-rows-max gap-6">
        <!-- Gender Select -->
        <div class="flex flex-col">
          <p class="text-2xl mb-2 text-teal-200">
            Gender
          </p>
          <div class="flex mx-1 items-center">
            <input
              v-model="stats.gender"
              class="mr-3"
              type="radio"
              name="gender"
              value="male"
              @change="calcBMR"
            >
            <label for="male">Male</label>
          </div>
          <div class="flex mx-1 items-center">
            <input
              v-model="stats.gender"
              class="mr-3"
              type="radio"
              name="gender"
              value="female"
              @change="calcBMR"
            >
            <label for="female">Female</label>
          </div>
        </div>
        <!-- Age -->
        <div>
          <p class="text-2xl mb-2 text-teal-200">
            Age
          </p>
          <input
            v-model="stats.age"
            min="1"
            class="border bg-transparent rounded-lg p-2 w-11/12"
            type="number"
            @change="calcBMR"
          >
        </div>
        <!-- Height -->
        <div>
          <p class="text-2xl mb-2 text-teal-200">
            Height
          </p>
          <!-- cm if isMetric -->
          <div v-if="stats.isMetric" class="grid">
            <span class="border bg-transparent rounded-lg p-2 flex items-center">
              <input
                v-model="stats.metric.height"
                min="1"
                class="bg-transparent"
                type="number"
                @change="calcBMR"
              >cm
            </span>
          </div>
          <div v-if="!stats.isMetric" class="grid grid-cols-2 gap-4">
            <!-- ft & in if !isMetric -->
            <span class="border bg-transparent rounded-lg p-2 flex items-center">
              <input
                v-model="feet"
                min="1"
                class="bg-transparent w-11/12"
                type="number"
                @change="calcBMR"
              >ft
            </span>
            <span class="border bg-transparent rounded-lg p-2 flex items-center">
              <input
                v-model="inches"
                min="1"
                class="bg-transparent w-11/12"
                type="number"
                @change="calcBMR"
              >in
            </span>
          </div>
        </div>
        <!-- Weight -->
        <div>
          <p class="text-2xl mb-2 text-teal-200">
            Weight
          </p>
          <span class="border bg-transparent rounded-lg p-2">
            <input
              v-model.number="stats.imperial.weight"
              min="1"
              class="bg-transparent p-2"
              type="number"
              @change="calcBMR"
            >
            <!-- kg if isMetric -->
            {{ stats.isMetric ? 'kg' : 'lbs' }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['stats'],
  data () {
    return {
      feet: 0,
      inches: 0,
      weight: 0
    }
  },
  methods: {
    calcBMR () {
      if (!this.stats.isMetric) {
        this.feetToInches()
      }
      this.$emit('calcBMR')
    },
    feetToInches () {
      const totalInches = (this.feet * 12) + parseInt(this.inches)
      this.stats.imperial.height = totalInches
    }
  }
}
</script>

<style>
  input[type=number]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
</style>
