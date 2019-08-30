<template>
  <div id="app" class="bg-gray-600 font-mono">
    <div class="container mx-auto min-h-screen">
      <div class="flex justify-center items-center">
        <form @submit.prevent="onSubmit" class="p-2">
          <div class="flex mb-2">
            <div class="flex items-center">
              <input v-model.number="inputX5" class="w-16 h-8 px-1 text-sm rounded" type="text">
              <label class="mx-1">x⁵ +</label>
            </div>
            <div class="flex items-center">
              <input v-model.number="inputX4" class="w-16 h-8 px-1 text-sm rounded" type="text">
              <label class="mx-1">x⁴ +</label>
            </div>
            <div class="flex items-center">
              <input v-model.number="inputX3" class="w-16 h-8 px-1 text-sm rounded" type="text">
              <label class="mx-1">x³ +</label>
            </div>
            <div class="flex items-center">
              <input v-model.number="inputX2" class="w-16 h-8 px-1 text-sm rounded" type="text">
              <label class="mx-1">x² +</label>
            </div>
            <div class="flex items-center">
              <input v-model.number="inputX1" class="w-16 h-8 px-1 text-sm rounded" type="text">
              <label class="mx-1">x +</label>
            </div>
            <div class="flex items-center">
              <input v-model.number="inputX" class="w-16 h-8 px-1 text-sm rounded" type="text">
              <label class="mx-1"></label>
            </div>
          </div>
          <div class="flex items-center my-6">
            <label class="mr-2">Epsilon</label>
            <input v-model.number="epsilon" class="w-16 h-8 px-1 text-sm rounded" type="text">
          </div>

          <button class="border rounded py-1 px-2" type="submit">Enviar</button>
        </form>
      </div>

      <div class="flex items-center mt-4">
        <table class="w-full text-left text-sm shadow-md">
          <thead class="bg-gray-800 text-white w-full flex rounded-t">
            <tr class="border-b flex justify-center w-full">
              <th class="p-2 w-1/4">Intervalo</th>
              <th class="p-2 w-1/4">Resultado da Funcao</th>
            </tr>
          </thead>
          <tbody class="flex flex-col items-center w-full">
            <tr v-for="(item, index) in data" :key="index" class="flex justify-center w-full border-b">
              <td class="p-2 w-1/4">[ {{ item.intervalo.a }}, {{ item.intervalo.a }} ]</td>
              <td class="p-2 w-1/4">{{ item.raizDaFuncao }}</td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="flex items-center justify-center mt-4">
        <table class="w-full text-left text-sm shadow-md">
          <thead class="bg-gray-800 text-white w-full flex rounded-t">
            <tr class="border-b flex justify-center w-full">
              <th class="p-2 w-1/4">a</th>
              <th class="p-2 w-1/4">b</th>
            </tr>
          </thead>
          <tbody class="flex flex-col items-center w-full">
            <tr v-for="(item, index) in data" :key="index" class="flex justify-center w-full border-b">
              <td class="p-2 w-1/4">{{ item.intervalosIniciais[0].a }}</td>
              <td class="p-2 w-1/4">{{ item.intervalosIniciais[0].b }}</td>
            </tr>
          </tbody>
        </table>
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
        epsilon: null,
        data: null
      }
    },

    methods: {
      async onSubmit() {
        this.data = []
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
        this.data = data
        console.log(data)
      }

    }
  }
</script>

<style src="./css/main.css">