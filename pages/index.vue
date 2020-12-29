<template>
  <div class="flex justify-center">
    <div class="grid grid-rows-2 lg:grid-cols-3 gap-4 mt-8 h-1/2 lg:w-3/4">
      <div class="grid grid-rows-4 lg:col-span-2 gap-4">
        <Stats :stats="stats" @calcBMR="calcBMR" />
        <ExerciseLevel @levelChange="updateLevel($event)" />
        <Goal :goal="goal" @updateGoal="updateGoal($event)" />
        <Macros ref="macros" :bmr="bmr.goal" />
      </div>
      <div class="lg:col-span-1">
        <Results :bmr="bmr" @updateBMR="calcBMR" />
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
        isMetric: false,
        imperial: {
          height: 0,
          weight: 0
        },
        metric: {
          height: 0,
          weight: 0
        }
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
      const kg = this.stats.imperial.weight / 2.205
      this.stats.metric.weight = parseInt(kg)
    },
    inchesToCm () {
      const cm = this.stats.imperial.height * 2.54
      this.stats.metric.height = cm
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
      const bmrWeight = 10 * this.stats.metric.weight
      const bmrHeight = 6.25 * this.stats.metric.height
      const bmrAge = 5 * this.stats.age
      const bmrGender = this.stats.gender === 'male' ? 5 : -161
      let newBMRTotal = bmrWeight + bmrHeight - bmrAge + bmrGender
      newBMRTotal = this.stats.gender === 'male' ? newBMRTotal + 5 : newBMRTotal - 161
      this.bmr.total = parseInt(newBMRTotal)
      this.calcGoalBMR()
    },
    calcGoalBMR () {
      const goalBMR = (this.bmr.total * this.level) + (this.bmr.total * this.goal)
      this.bmr.goal = Math.floor(parseFloat(goalBMR))
      this.$refs.macros.updateMacros()
    }
  }
}
</script>
