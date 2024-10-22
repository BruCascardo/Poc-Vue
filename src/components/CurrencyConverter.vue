<template>
  <div class="currency-converter">
    <h2>Currency Converter</h2>
    <div>
      <input type="number" v-model.number="amount" placeholder="Enter amount" />
      <select v-model="fromCurrency">
        <option v-for="currency in currencies" :key="currency" :value="currency">
          {{ currency }}
        </option>
      </select>
      <span> to </span>
      <select v-model="toCurrency">
        <option v-for="currency in currencies" :key="currency" :value="currency">
          {{ currency }}
        </option>
      </select>
    </div>
    <button @click="convertCurrency" style="margin-top: 10px">Convert</button>
    <div v-if="result" style="margin-top: 20px">
      <h3>{{ amount }} {{ fromCurrency }} = {{ result }} {{ toCurrency }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CurrencyConverter',
  data() {
    return {
      amount: 1,
      fromCurrency: 'USD',
      toCurrency: 'PESOS',
      currencies: ['USD', 'PESOS'],
      result: null,
    };
  },
  methods: {
    convertCurrency() {
      let exchangeRate;

      // Conversion logic
      if (this.fromCurrency === 'PESOS' && this.toCurrency === 'USD') {
        exchangeRate = 1 / 1200;
      } else if (this.fromCurrency === 'USD' && this.toCurrency === 'PESOS') {
        exchangeRate = 1200;
      } else {
        exchangeRate = 1;
      }

      this.result = (this.amount * exchangeRate).toFixed(2);
    },
  },
};
</script>

<style scoped>
.currency-converter {
  text-align: center;
  padding: 20px;
  background-color: pink;
  border-radius: 8px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
}

button {
  margin-top: 10px;
  padding: 10px 20px;
  background-color: blueviolet;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
