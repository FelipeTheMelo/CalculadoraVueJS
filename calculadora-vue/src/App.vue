<template>
  <div class="calculator">
    <h1>Calculadora Aritmética</h1>
    <input v-model.number="numero1" type="number" placeholder="Número 1" />
    <input v-model.number="numero2" type="number" placeholder="Número 2" />

    <select v-model="operacao">
      <option value="+">Soma (+)</option>
      <option value="-">Subtração (-)</option>
      <option value="*">Multiplicação (*)</option>
      <option value="/">Divisão (/)</option>
    </select>

    <p class="resultado">
      Resultado: <strong>{{ resultado }}</strong>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
    };
  },
  computed: {
    resultado() {
      switch (this.operacao) {
        case '+':
          return this.numero1 + this.numero2;
        case '-':
          return this.numero1 - this.numero2;
        case '*':
          return this.numero1 * this.numero2;
        case '/':
          return this.numero2 !== 0
            ? (this.numero1 / this.numero2).toFixed(2)
            : 'Erro (divisão por zero)';
        default:
          return 0;
      }
    },
  },
};
</script>

<style>
.calculator {
  max-width: 300px;
  margin: 50px auto;
  padding: 20px;
  border: 2px solid #4f46e5;
  border-radius: 10px;
  text-align: center;
  font-family: sans-serif;
}

input,
select {
  margin: 10px 0;
  padding: 5px;
}
</style>