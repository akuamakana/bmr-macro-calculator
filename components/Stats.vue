<template>
  <div class="bg-gray-700 rounded-lg flex w-full p-6 shadow-lg">
    <div class="flex items-center w-full">
      <div class="flex justify-between w-full gap-4">
        <!-- Gender Select -->
        <div class="flex flex-col">
          <p class="text-center text-2xl mb-2 text-teal-200">
            Gender
          </p>
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
          <p class="text-center text-2xl mb-2 text-teal-200">
            Height
          </p>
          <input class="border bg-transparent rounded-lg p-2 w-32 " type="number" placeholder="69">
        </div>
        <!-- Age -->
        <div>
          <p class="text-center text-2xl mb-2 text-teal-200">
            Age
          </p>
          <input class="border bg-transparent rounded-lg p-2 w-32 " type="number" placeholder="69">
        </div>
        <!-- Weight -->
        <div>
          <p class="text-center text-2xl mb-2 text-teal-200">
            Weight
          </p>
          <input class="border bg-transparent rounded-lg p-2 w-32 " type="number" placeholder="69">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
}
</script>
