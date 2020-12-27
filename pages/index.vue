<template>
  <div class="container grid grid-cols-2">
    <div class="grid grid-rows-3">
      <Stats />
      <ExerciseLevel />
      <Goal />
    </div>
    <div>
      <Results />
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
