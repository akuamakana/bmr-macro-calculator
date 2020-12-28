<template>
  <div class="flex justify-center">
    <div class="grid grid-cols-3 gap-4 mt-8 h-1/2 w-3/4">
      <div class="grid grid-rows-3 col-span-2 gap-4">
        <Stats :stats="stats" @calcBMR="calcBMR" />
        <ExerciseLevel @levelChange="updateLevel($event)" />
        <Goal :goal="goal" @updateGoal="updateGoal($event)" />
      </div>
      <div class="col-span-1">
        <Results :bmr="bmr" />
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
  components: Stats,
  ExerciseLevel,
  Goal,
  Results,
  data () {
    return {
      stats: {
        gender: 'male',
        age: 25,
        height: 59,
        weight: 200
      },
      bmr: {
        total: 2000,
        goal: 3000
      },
      level: 1.55,
      goal: 0
    }
  },
  methods: {
    lbsToKg () {
      const kg = this.stats.weight / 2.205
      return kg
    },
    inchesToCm () {
      const cm = this.stats.height * 2.54
      return cm
    },
    updateLevel (level) {
      this.level = level
      this.calcBMR()
    },
    updateGoal (goal) {
      console.log('goal')
      this.goal = goal
      this.calcBMR()
    },
    calcBMR () {
      // BMR = (10 × weight in kg) + (6.25 × height in cm) - (5 × age in years) + 5
      // BMR = (10 × weight in kg) + (6.25 × height in cm) - (5 × age in years) - 161
      const bmrWeight = 10 * this.lbsToKg()
      const bmrHeight = 6.25 * this.inchesToCm()
      const bmrAge = 5 * this.stats.age
      const bmrGender = this.stats.gender === 'male' ? 5 : -161
      const newBMRTotal = bmrWeight + bmrHeight - bmrAge + bmrGender * this.level
      this.bmr.total = parseInt(newBMRTotal)
      this.calcGoalBMR()
    },
    calcGoalBMR () {
      const goalBMR = this.bmr.total + (this.bmr.total * this.goal)
      this.bmr.goal = parseInt(goalBMR)
    }
  }
}
</script>
