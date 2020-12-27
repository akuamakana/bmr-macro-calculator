<template>
  <div class="bg-gray-700 rounded-lg flex p-6">
    <div class="flex items-center">
      <div class="grid grid-flow-col gap-4">
        <!-- Gender Select -->
        <div class="flex flex-col">
          <p>Gender:</p>
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
        <div>
          <p>Height</p>
          <input class="border bg-transparent rounded-lg p-2" type="number" placeholder="69">
        </div>
        <!-- Age -->
        <div>
          <p>Age</p>
          <input class="border bg-transparent rounded-lg p-2" type="number" placeholder="69">
        </div>
        <!-- Weight -->
        <div>
          <p>Weight</p>
          <input class="border bg-transparent rounded-lg p-2" type="number" placeholder="69">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
}
</script>
