<template>
  <div class="bg-gray-700 rounded-lg flex flex-col w-full p-6 shadow-lg">
    <h1 class="block text-3xl text-teal-200 font-bold mb-2">
      Goal
    </h1>
    <div class="flex justify-around h-full">
      <div class="flex justify-between items-center">
        <input
          v-model="goal"
          type="radio"
          name="goal"
          value="-0.1"
          class="mr-3"
          @change="updateGoal"
        >
        <label for="goal">Lose</label>
      </div>
      <div class="flex justify-between items-center">
        <input
          v-model="goal"
          type="radio"
          name="goal"
          value="0"
          class="mr-3"
          @change="updateGoal"
        >
        <label for="goal">Maintain</label>
      </div>
      <div class="flex justify-between items-center">
        <input
          v-model="goal"
          type="radio"
          name="goal"
          value="0.1"
          class="mr-3"
          @change="updateGoal"
        >
        <label for="goal">Gain</label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      goal: 0
    }
  },
  methods: {
    updateGoal () {
      this.$emit('updateGoal', this.goal)
    }
  }
}
</script>
