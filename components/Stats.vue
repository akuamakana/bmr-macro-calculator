<template>
  <div class="bg-gray-700 rounded-lg flex w-full p-6 shadow-lg">
    <div class="flex items-center w-full">
      <div class="flex justify-between w-full gap-4">
        <!-- Gender Select -->
        <div class="flex flex-col">
          <p class="text-center text-2xl mb-2 text-teal-200">
            Gender
          </p>
          <div class="flex mx-1">
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
          <div class="flex mx-1">
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
          <p class="text-center text-2xl mb-2 text-teal-200">
            Age
          </p>
          <input v-model="stats.age" class="border bg-transparent rounded-lg p-2 w-32 " type="number" placeholder="69" @change="calcBMR">
        </div>
        <!-- Height -->
        <div>
          <p class="text-center text-2xl mb-2 text-teal-200">
            Height
          </p>
          <input v-model="stats.height" class="border bg-transparent rounded-lg p-2 w-32 " type="number" placeholder="69" @change="calcBMR">
        </div>
        <!-- Weight -->
        <div>
          <p class="text-center text-2xl mb-2 text-teal-200">
            Weight
          </p>
          <input v-model="stats.weight" class="border bg-transparent rounded-lg p-2 w-32 " type="number" placeholder="69" @change="calcBMR">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['stats'],
  methods: {
    calcBMR () {
      this.$emit('calcBMR')
    }
  }
}
</script>

<style>
  input[type=number]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}
</style>
