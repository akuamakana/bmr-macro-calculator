<template>
  <div class="border bg-red-500 rounded-lg flex p-6">
    <div class="flex items-center">
      <!-- Gender Select -->
      <div class="flex flex-row">
        <div class="flex mx-1">
          <input class="mr-1" type="radio" name="gender" value="male">
          <label for="male">Male</label>
        </div>
        <div class="flex mx-1">
          <input class="mr-1" type="radio" name="gender" value="female">
          <label for="female">Female</label>
        </div>
      </div>
      <!-- Height -->
      <input class="border w-24 mx-2 rounded-lg p-2" type="number" placeholder="69">
      <!-- Age -->
      <input class="border w-24 mx-2 rounded-lg p-2" type="number" placeholder="69">
      <!-- Weight -->
      <input class="border w-24 mx-2 rounded-lg p-2" type="number" placeholder="69">
    </div>
  </div>
  </div>
</template>

<script>
import CardWrapper from '~/components/CardWrapper'
export default {
  components: CardWrapper
}
</script>
