<template>
  <div class="bg-purple-500 w-screen p-10">
    <div class="bg-gray-200 shadow-2xl text-gray-800 w-full xl:w-6/12 p-10 mx-auto rounded-lg my-6">
    <img src="https://ici.earth/wp-content/uploads/2019/12/ICI_Logo_Green_v4.png" alt="" class="text-center w-24 mx-auto">
      <h1 class="text-center text-xl xl:text-3xl">
        Welcome to 44by12
      </h1>
      <p class="text-center mb-6"> A quick footprint calculator</p>
      <p class="text-center">
        44by12 is an quick, snappy and on-the-go carbon footprint calculator. You can simply select various materials
        and services and enter the required and voila ! There you have it you have it, the footprint for the selected
        material or service.
        <br>
        <br>
        44by12 also returns a contextual value, in terms of 'number of trees choped off', that can help you visualize
        the impact of you selected service/material
      </p>
      <br>
      <p class="text-xs text-right">Emission factors are sourced from Defra 2019</p>
    </div>
    <div class="bg-gray-800 p-10 mx-auto w-full xl:w-6/12 shadow-2xl rounded-lg mb-6">
      <label for="" class="text-white">Resulting emissions: <small class="text-xs">(kgCO2e)</small></label>
      <input type="text" readonly class="rounded p-2 w-full bg-gray-900 text-white text-right text-xl outline-none"
        v-model="footprint">
      <div class="my-6 grid grid-cols-1 xl:grid-cols-2 gap-6 xl:gap-6">
        <div>
          <label for="" class="text-white">Select your material:</label>
          <select name="" id="" class="w-full p-2 h-10 appearance-none outline-none bg-gray-900 text-white"
            v-model="materialValue" @change="calculateFootprint">
            <optgroup label="Construction Materials">
              <option v-for="material in constructionMaterials" :key="material.id" :value="material.value">
                {{material.name}}</option>
            </optgroup>
            <optgroup label="Useables">
              <option v-for="material in useables" :key="material.id" :value="material.value">{{material.name}}</option>
            </optgroup>
          </select>
        </div>
        <div>
          <label for="" class="text-white">Enter the amount: <small class="text-xs">(tonnes)</small></label>
          <input type="text" class="rounded p-2 h-10 w-full bg-gray-900 text-white text-right text-xl outline-none"
            v-model="inputValue" @input="calculateFootprint">
        </div>
      </div>
      <div class="">
           <input type="text" readonly class="rounded p-2 w-full bg-gray-900 text-white text-right text-xl outline-none"
        v-model="trees">
        </div>
    </div>
  </div>
</template>

<script>
  export default {
    data: function () {
      return {
        footprint: 0,
        inputValue: "",
        materialValue: "",
        trees:"",
        constructionMaterials: [{
            id: 1,
            name: '🥌 Aggregates',
            value: 7.7944
          },
          {
            id: 2,
            name: '🏗 Average construction',
            value: 69.2698
          },
          {
            id: 3,
            name: '📏 Asbestos',
            value: 27
          },
          {
            id: 4,
            name: '🛣 Asphalt',
            value: 39.21
          },
          {
            id: 5,
            name: '🧱 Bricks',
            value: 241.79
          },
          {
            id: 6,
            name: '🏎 Concrete',
            value: 131.79
          }
        ],
        useables: [{
            id: 1,
            name: "📚 Books",
            value: 952.68
          },
          {
            id: 2,
            name: "🥂 Glass",
            value: 895
          },
          {
            id: 3,
            name: "🥼👗 Clothing",
            value: 22310
          },
          {
            id: 4,
            name: "🍟🍺 Food and drinks",
            value: 4060.1636
          },
        ],

      }
    },
    methods: {
      calculateFootprint() {
         this.footprint = Math.round(this.inputValue * this.materialValue)
         return this.trees = Math.round(this.footprint/0.25) + ` 🌳🌳🌳🌳🌳`
      }
    },
    components: {

    }
  }

</script>

<style>
  /* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
  @import url('https://fonts.googleapis.com/css?family=Nunito&display=swap');

  body {
    font-family: 'Nunito', sans-serif;
  }

</style>
