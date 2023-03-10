<script setup>
import { reactive } from 'vue';

const estado = reactive({
  number: 0,
  secondNumber: 0,
  operatorType: 'Selecione'
})
  function calc(a, b, op){
      const valor1 = parseInt(a);
      const valor2 = parseInt(b);


    if(op === "+"){
      return valor1 + valor2;
    }if (op=== "-"){
      return valor1 - valor2;
    } if (op === "*"){
      return valor1 * valor2;
    } if(op === '/'){
      return valor1 / valor2;
    } if(op === "%"){
      return valor1 % valor2;
    }
  }

  function operator(a, b) {
    const number1 = parseInt(a);
    const number2 = parseInt(b);
    
    return number1 + number2;
  }
</script>

<template>
  <div class="container">
    <header>
      <h1>Calculadora</h1>
    </header>
    <br>
    <hr>
    <div class="contador">
      Resultado: {{ calc(estado.number, estado.secondNumber, estado.operatorType) }} <br>
      Operador: {{ estado.operatorType }}
    </div>
   

      
      <div class="calc">
        <input placeholder="Digite o primeiro número" type="number" @keyup="evento => estado.number = evento.target.value"><br>

        <div class="calcContainer">
      <select @change="evento => estado.operatorType = evento.target.value">
        <option value="">Selecione</option>
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
        <option value="%">%</option>


      </select>
      <br>

        <input placeholder="digite o segundo número" type="number" @keyup="evento => estado.secondNumber = evento.target.value">
      </div>
    </div>
  </div>
</template>

<style scoped>


.container{
    width: 100vw;
    padding-top: 100px;
    height: 500px;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: #023047;
    color: #fff;
  }

  .calc{
    display: grid;
    margin: 16px auto 0 auto;
    grid-template-columns:1fr;

  }
  .contador{
    font-size: 24px;
    margin-bottom: 16px;
  }
  select{
    margin: 0 auto 20px auto;
  }
  input {
    border-radius: 4px;
    background: rgba(0,0,0,.2);
    border: 1px solid #000;
    color: #fff;
  }
</style>
