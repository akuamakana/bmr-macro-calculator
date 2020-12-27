<template>
  <div class="flex justify-center w-screen">
    <div class="grid grid-cols-2 mt-8 w-2/3">
      <div class="grid grid-rows-3 gap-4">
        <Stats />
        <ExerciseLevel />
        <Goal />
      </div>
      <div>
        <Results />
      </div>
    </div>
  </div>
</template>

<script>
import Stats from '~/components/Stats'
import ExerciseLevel from '~/components/ExerciseLevel'
import Goal from '~/components/Goal'
import Results from '~/components/Results'
export default {
  components: Stats, ExerciseLevel, Goal, Results
}
</script>
