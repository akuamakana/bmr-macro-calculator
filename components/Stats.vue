<template>
  <div class="bg-gray-700 rounded-lg flex p-6">
    <div class="flex items-center">
      <!-- Gender Select -->
      <div class="flex flex-col">
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
      <input class="border mx-2 rounded-lg p-2" type="number" placeholder="69">
      <!-- Age -->
      <input class="border mx-2 rounded-lg p-2" type="number" placeholder="69">
      <!-- Weight -->
      <input class="border mx-2 rounded-lg p-2" type="number" placeholder="69">
    </div>
  </div>
  </div>
</template>

<script>
export default {
}
</script>
