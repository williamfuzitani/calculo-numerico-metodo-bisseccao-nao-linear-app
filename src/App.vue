<template>
  <div id="app">

    <section style="display: block">
      <span>f(x) =</span> 
      <input v-model="inputX5" type="number">x^5 +
      <input v-model="inputX4" type="number">x^4 +
      <input v-model="inputX3" type="number">x^3 +
      <input v-model="inputX2" type="number">x^2 +
      <input v-model="inputX1" type="number">x +
      <input v-model="inputX" type="number">
    </section>

    <section style="display: block">
      <span>E = 10^</span>
      <input v-model="epsilon" type="number">
    </section>

    <button type="submit">Enviar</button>

    <section>
      <h1>Resultado</h1>
      <div>
        <span>
          Intervalos
        </span>
      </div>
      <div>
        <span>
          Raizes
        </span>
      </div>
      <div>
        <span>
          Tabela
        </span>
      </div>
    </section>

  </div>
</template>

<script>
export default {
  name: 'app',
  data: () =>({
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
    inputX:  {
      type: Number,
      required: true
    },
    epsilon: {
      type: Number,
      required: true
    }
  }),

  computed: {
    
  },

  methods: {

  }
}
</script>

<style />
