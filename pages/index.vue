<template>
  <div class="flex justify-center">
    <div class="grid grid-cols-3 gap-4 mt-8 h-1/2 w-3/4">
      <div class="grid grid-rows-4 col-span-2 gap-4">
        <Stats :stats="stats" @calcBMR="calcBMR" />
        <ExerciseLevel @levelChange="updateLevel($event)" />
        <Goal :goal="goal" @updateGoal="updateGoal($event)" />
        <Macros ref="macros" :bmr="bmr.goal" />
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
import Macros from '~/components/Macros'
export default {
  components: Stats,
  ExerciseLevel,
  Goal,
  Results,
  Macros,
  data () {
    return {
      stats: {
        gender: 'male',
        age: 25,
        heightInCm: 59,
        heightInIn: 69,
        weight: 200,
        isMetric: false
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
      this.stats.weight = parseInt(kg)
    },
    inchesToCm () {
      const cm = this.stats.heightInIn * 2.54
      this.stats.heightInCm = cm
    },
    updateLevel (level) {
      this.level = level
      this.calcBMR()
    },
    updateGoal (goal) {
      this.goal = goal
      this.calcBMR()
    },
    imperialToMetric () {
      if (this.stats.isMetric) {
        return
      }
      this.lbsToKg()
      this.inchesToCm()
    },
    calcBMR () {
      // BMR = (10 × weight in kg) + (6.25 × height in cm) - (5 × age in years) + 5
      // BMR = (10 × weight in kg) + (6.25 × height in cm) - (5 × age in years) - 161
      this.imperialToMetric()
      const bmrWeight = 10 * this.stats.weight
      const bmrHeight = 6.25 * this.stats.heightInCm
      const bmrAge = 5 * this.stats.age
      const bmrGender = this.stats.gender === 'male' ? 5 : -161
      const newBMRTotal = bmrWeight + bmrHeight - bmrAge + bmrGender
      this.bmr.total = parseInt(newBMRTotal)
      this.calcGoalBMR()
      this.$refs.macros.updateMacros()
    },
    calcGoalBMR () {
      const goalBMR = (this.bmr.total * this.level) + (this.bmr.total * this.goal)
      this.bmr.goal = parseInt(goalBMR)
    }
  }
}
</script>
