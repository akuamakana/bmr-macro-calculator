<template>
  <div class="bg-gray-700 rounded-lg grid grid-rows-2 gap-6 text-center h-full shadow-lg p-6">
    <div class="border-2 border-gray-200 border-opacity-50 rounded-lg w-max h-full flex flex-col justify-center">
      <h1 class="text-3xl text-teal-200 font-bold">BMR:</h1>
      <h1 class="text-3xl">{{ bmr.total }} Calories</h1>
    </div>
    <div class="border-2 border-gray-200 border-opacity-50 rounded-lg w-max h-full flex flex-col justify-center">
      <h1 class="text-3xl text-teal-200 font-bold">Goal BMR:</h1>
      <h1 class="text-3xl">{{ bmr.goal }} Calories</h1>
    </div>
  </div>
</template>

<script>
export default {
  props: ['bmr']
}
</script>
