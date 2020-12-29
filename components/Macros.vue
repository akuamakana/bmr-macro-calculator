<template>
  <div class="bg-gray-700 rounded-lg flex flex-col w-full p-6 shadow-lg">
    <h1 class="block text-3xl text-teal-200 font-bold mb-2">
      Macros
    </h1>
    <div class="flex justify-around h-full">
      <div class="flex flex-col">
        <h1 class="text-2xl mb-2 text-teal-200">
          Carbs: {{ macros.carbs }} grams
        </h1>
        <span class="border bg-transparent rounded-lg p-2 flex justify-between">
          <input
            v-model="percentage.carbs"
            min="0"
            max="100"
            type="number"
            class="bg-transparent focus:outline-none w-full"
            @change="updateMacros"
          >%
        </span>
      </div>
      <div class="flex flex-col">
        <h1 class="text-2xl mb-2 text-teal-200">
          Proteins: {{ macros.protein }} grams
        </h1>
        <span class="border bg-transparent rounded-lg p-2 flex justify-between">
          <input
            v-model="percentage.protein"
            min="0"
            max="100"
            type="number"
            class="bg-transparent focus:outline-none w-full"
            @change="updateMacros"
          >%
        </span>
      </div>
      <div class="flex flex-col">
        <h1 class="text-2xl mb-2 text-teal-200">
          Fats: {{ macros.fats }} grams
        </h1>
        <span class="border bg-transparent rounded-lg p-2 flex justify-between">
          <input
            v-model="percentage.fats"
            min="0"
            max="100"
            type="number"
            class="bg-transparent w-full focus:outline-none"
            @change="updateMacros"
          >%
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['bmr'],
  data () {
    return {
      percentage: {
        carbs: 40,
        protein: 40,
        fats: 20
      },
      macros: {
        carbs: 0,
        protein: 0,
        fats: 0
      }
    }
  },
  methods: {
    updateMacros () {
      const carbs = this.bmr * (this.percentage.carbs / 100) / 4
      const protein = this.bmr * (this.percentage.protein / 100) / 4
      const fats = this.bmr * (this.percentage.fats / 100) / 9
      this.macros.carbs = parseInt(carbs)
      this.macros.protein = parseInt(protein)
      this.macros.fats = parseInt(fats)
    }
  }
}
</script>
