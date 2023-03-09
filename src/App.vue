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
      Numero 1: {{ estado.number }} <br>
      Numero 2:{{ estado.secondNumber }} <br>
      Resultado: {{ calc(estado.number, estado.secondNumber, estado.operatorType) }} <br>
      Operador: {{ estado.operatorType }}
    </div>
    <div class="calcContainer">
      <select @change="evento => estado.operatorType = evento.target.value">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
        <option value="%">%</option>


      </select>
      <br>

      
      <div class="calc">
        <input type="number" @keyup="evento => estado.number = evento.target.value"><br>
        <input type="number" @keyup="evento => estado.secondNumber = evento.target.value">
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
  .number{
    width: 50px;
    height: 30px;
    border: 1px solid #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
    background-color: transparent;
    color: #fff;
  }
  .number:hover{
    cursor: pointer;
  }
  .calc{
    display: grid;
    margin: 16px auto;
    grid-template-columns:1fr;

  }
  .contador{
    font-size: 24px;
    margin-bottom: 16px;
  }
  input{
    border-radius: 4px;
    background: rgba(0,0,0,.2);
    border: 1px solid #000;
    color: #fff;
  }
</style>
