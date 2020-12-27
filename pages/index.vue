<template>
  <div class="flex justify-center">
    <div class="grid grid-cols-3 gap-4 mt-8 h-1/2">
      <div class="grid grid-rows-3 col-span-2 gap-4">
        <Stats />
        <ExerciseLevel />
        <Goal />
      </div>
      <div class="col-span-1">
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
