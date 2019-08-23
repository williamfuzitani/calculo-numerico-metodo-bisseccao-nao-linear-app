<template>
  <div>
    <div>f(x) = 
      <input v-model="inputX5" type="text">x^5 +
      <input v-model="inputX4" type="text">x^4 +
      <input v-model="inputX3" type="text">x^3 +
      <input v-model="inputX2" type="text">x^2 +
      <input v-model="inputX1" type="text">x +
      <input v-model="inputX" type="text">
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () =>({
    inputX5: null,
    inputX4: null,
    inputX3: null,
    inputX2: null,
    inputX1: null,
    inputX:  null,
  }),

  methods: {
    soma() {
      return inputX5 + inputX4 + inputX3 + inputX2 + inputX1 + inputX
    }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}


</style>
