<script setup>
  import { reactive } from 'vue';

  const numero = reactive({
    campo1: 0,
    campo2: 0,
    operator: "+",
    result: 0
  })

  function aritmetica(){
    const n1 = parseFloat(numero.campo1)
    const n2 = parseFloat(numero.campo2)

    switch (numero.operator) {
      case '+':
        numero.result = n1 + n2;
        break;

      case '-':
        numero.result = n1 - n2;
        break;

      case 'x':
        numero.result = n1 * n2;
        break;
      
      case '÷':
        numero.result = n2 !== 0? n2  / n2: "Não é possível dividir por 0";
        break;
    }
  }
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light">
      <h1>Aritmética</h1>
      <p>
        Selecione 2 valores e um operador para ver o resultado imediatamente!
      </p>
    </header>
    <form>
      <div class="row">
        <div class="col-md-3">
          <input @keyup="e => {numero.campo1 = e.target.value; aritmetica()}" type="number" class="form-control" placeholder="0">
        </div>
        <div class="col-md-1">
          <select @change="e => {numero.operator = e.target.value; aritmetica()}" class="form-control text-center">
            <option>+</option>
            <option>-</option>
            <option>x</option>
            <option>÷</option>
          </select>
        </div>
        <div class="col-md-3">
          <input @keyup="e => {numero.campo2 = e.target.value; aritmetica()}" type="number" class="form-control" placeholder="0">
        </div>
      </div>
    </form>
    <div class="resultado mt-4 pb-4">
      <p class="h5">Resultado: {{ numero.result }}</p>
    </div>
  </div>
</template>

<style>
html {
  background-color: rgb(112, 112, 112);
}
</style>
