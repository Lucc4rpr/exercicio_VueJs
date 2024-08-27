<template>
<div class="container">

    
    <div id="app">
      <h1>Calculadora</h1>
      <div class="calculator">
        <div class="form-group">
          <label for="num1">Digite o Primeiro Valor</label>
          <input id="num1" type="number" v-model.number="num1" />
        </div>
        
        <div class="form-group">
          <label for="num2">Digite o Segundo Valor</label>
          <input id="num2" type="number" v-model.number="num2" />
        </div>
        
        <div class="form-group">
          <label for="operation">Operação:</label>
          <select id="operation" v-model="operation">
            <option value="+">Soma</option>
            <option value="-">Subtração</option>
            <option value="*">Multiplicação</option>
            <option value="/">Divisão</option>
          </select>
        </div>
  
        <div class="result">
          <h2>Resultado: {{ resultado }}</h2>
        </div>
      </div>
    </div>
</div>
  </template>
  
  <script setup>
  import { computed, ref } from 'vue';
  
  const num1 = ref(0);
  const num2 = ref(0);
  const operation = ref('+');
  
  const resultado = computed(() => {
    switch (operation.value) {
      case '+':
        return num1.value + num2.value;
      case '-':
        return num1.value - num2.value;
      case '*':
        return num1.value * num2.value;
      case '/':
        return num2.value !== 0 ? num1.value / num2.value : 'Divisão por zero';
      default:
        return 0;
    }
  });
  </script>
  
  <style scoped>

  .container {
    max-width: 600px;
    height: 100vh;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .calculator {
    max-width: 100%;
    margin:  auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }
  
  .form-group {
    margin-bottom: 10px;
  }
  
  input,
  select {
    width: 100%;
    padding: 8px;
    margin-top: 4px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }
  
  .result {
    margin-top: 20px;
    text-align: center;
  }
  
  h2 {
    color: #333;
  }
  </style>
  

