<template>
  <div id="app" class="min-h-screen bg-gray-600 font-mono">
    <div class="container mx-auto pt-12">
      <div class="flex justify-center">
        <form @submit.prevent="onSubmit" class="p-2 w-full">
          <div class="flex mb-2">
            <div class="flex items-center">
              <input v-model="inputX5" class="w-20 px-1 text-sm rounded" type="text">
              <label class="mx-1">x⁵ +</label>
            </div>
            <div class="flex items-center">
              <input v-model="inputX4" class="w-20 px-1 text-sm rounded" type="text">
              <label class="mx-1">x⁴ +</label>
            </div>
            <div class="flex items-center">
              <input v-model="inputX3" class="w-20 px-1 text-sm rounded" type="text">
              <label class="mx-1">x³ +</label>
            </div>
            <div class="flex items-center">
              <input v-model="inputX2" class="w-20 px-1 text-sm rounded" type="text">
              <label class="mx-1">x² +</label>
            </div>
            <div class="flex items-center">
              <input v-model="inputX1" class="w-20 px-1 text-sm rounded" type="text">
              <label class="mx-1">x +</label>
            </div>
            <div class="flex items-center">
              <input v-model="inputX" class="w-20 px-1 text-sm rounded" type="text">
              <label class="mx-1"></label>
            </div>
          </div>
          <div class="flex items-center my-6">
            <label class="mr-2">Epsilon</label>
            <input v-model="epsilon" class="w-20 px-1 text-sm rounded" type="text">
          </div>

          <button class="border rounded py-1 px-2" type="submit">Enviar</button>
        </form>
      </div>

      <div class="flex items-center justify-around mt-4 border rounded p-2">
        <div class="border rounded p-2">Intervalos</div>
        <div class="border rounded p-2">Raizes</div>
        <div class="border rounded p-2">Tabela</div>
      </div>
    </div>

  </div>
</template>

<script>
  /* eslint-disable */
  export default {
    name: 'app',
    data() {
      return {
        inputX5: null,
        inputX4: null,
        inputX3: null,
        inputX2: null,
        inputX1: null,
        inputX: null,
        epsilon: null
      }
    },

    methods: {
      async onSubmit() {
        const BASE_URL = 'https://calculo-numerico.herokuapp.com/api/calculo-numerico'
        const reqBody = {
          "entradaSeis": this.inputX5,
          "entradaCinco": this.inputX4,
          "entradaQuatro": this.inputX3,
          "entradaTres": this.inputX2,
          "entradaDois": this.inputX1,
          "entradaUm": this.inputX,
          "entradaEpsilon": this.epsilon
        }
        const options = {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify(reqBody)
        }

        const response = await fetch(BASE_URL, options)
        const data = await response.json()
        console.log(data)
      }

    }
  }
</script>

<style src="./css/main.css">