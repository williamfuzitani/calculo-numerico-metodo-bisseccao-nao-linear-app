<template>
  <div id="app" class="min-h-screen flex flex-col justify-center items-center bg-gray-600">
    <div class="border rounded">
      <form @submit.prevent="onSubmit" class="w-full p-2">
        <div class="flex mb-2">
          <div class="flex items-center">
            <input v-model="inputX5" class="w-16 px-1 text-sm" type="number">
            <label class="mx-2">x^5 +</label>
          </div>
          <div class="flex items-center">
            <input v-model="inputX4" class="w-16 px-1 text-sm" type="number">
            <label class="mx-2">x^4 +</label>
          </div>
          <div class="flex items-center">
            <input v-model="inputX3" class="w-16 px-1 text-sm" type="number">
            <label class="mx-2">x^3 +</label>
          </div>
          <div class="flex items-center">
            <input v-model="inputX2" class="w-16 px-1 text-sm" type="number">
            <label class="mx-2">x^2 +</label>
          </div>
          <div class="flex items-center">
            <input v-model="inputX1" class="w-16 px-1 text-sm" type="number">
            <label class="mx-2">x +</label>
          </div>
          <div class="flex items-center">
            <input v-model="inputX" class="w-16 px-1 text-sm" type="number">
            <label class="mx-2"></label>
          </div>
        </div>
        <div class="flex items-center my-6">
          <label class="">Epsilon</label>
          <input v-model="epsilon" class="w-16 px-1 text-sm" type="number">
        </div>

        <button class="border rounded py-1 px-2" type="submit">Enviar</button>
      </form>
    </div>

    <div class="flex items-center justify-around mt-2">
      <div class="border rounded p-2">Intervalos</div>
      <div class="border rounded p-2">Raizes</div>
      <div class="border rounded p-2">Tabela</div>
    </div>

  </div>
</template>

<script>
  import axios from 'axios'
  /* eslint-disable */
  export default {
    name: 'app',
    data() {
      return {
        inputX5: {
          type: Number,
          required: true
        },
        inputX4: {
          type: Number,
          required: true
        },
        inputX3: {
          type: Number,
          required: true
        },
        inputX2: {
          type: Number,
          required: true
        },
        inputX1: {
          type: Number,
          required: true
        },
        inputX: {
          type: Number,
          required: true
        },
        epsilon: {
          type: Number,
          required: true
        }
      }
    },

    methods: {
      async onSubmit() {
        console.log('submit')
        const BASE_URL = 'https://calculo-numerico.herokuapp.com/api/calculo-numerico'
        let reqData = {
          inputX5: this.inputX5,
          inputX4: this.inputX4,
          inputX3: this.inputX3,
          inputX2: this.inputX2,
          inputX1: this.inputX1,
          inputX: this.inputX,
          inputEpsilon: this.epsilon
        }

        await axios({
          method: 'post',
          url: BASE_URL,
          headers: {
            "Content-Type": "application/json",
            'Access-Control-Allow-Origin' : '*'
          },
          body: JSON.stringify(reqData)
        }).then(function (response) {
          console.log(response)
        }).catch(function (error) {
          console.log(error)
        })
      }

    }
  }
</script>

<style src="./css/main.css">