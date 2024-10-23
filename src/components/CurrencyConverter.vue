<template>
  <div class="currency-converter">
    <h2>Conversor de moneda</h2>
    <div class="input-group">
      <input type="number" v-model.number="amount" placeholder="Enter amount" />
      <select v-model="fromCurrency" class="select_value">
        <option v-for="currency in currencies" :key="currency.code" :value="currency.code">
          {{ currency.flag }} {{ currency.name }}
        </option>
      </select>
      <span class="to-text">to</span>
      <select v-model="toCurrency" class="select_value">
        <option v-for="currency in currencies" :key="currency.code" :value="currency.code">
          {{ currency.flag }} {{ currency.name }}
        </option>
      </select>
    </div>
    <button @click="convertCurrency">Convert</button>
    <div v-if="result" class="result">
      <h3>{{ amount }} {{ formatCurrency(fromCurrency) }} = {{ result }} {{ formatCurrency(toCurrency) }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Conversor de moneda',
  data() {
    return {
      amount: 1,
      fromCurrency: 'USD',
      toCurrency: 'PESOS',
      currencies: [
        { code: 'USD', name: 'USD', flag: '🇺🇸' },
        { code: 'PESOS', name: 'PESOS', flag: '🇦🇷' },
      ],
      result: null,
    };
  },
  methods: {
    convertCurrency() {
      let exchangeRate;

      if (this.fromCurrency === 'PESOS' && this.toCurrency === 'USD') {
        exchangeRate = 1 / 1200;
      } else if (this.fromCurrency === 'USD' && this.toCurrency === 'PESOS') {
        exchangeRate = 1200;
      } else {
        exchangeRate = 1;
      }

      const convertedAmount = this.amount * exchangeRate;

      this.result = convertedAmount.toLocaleString('de-DE', {
        minimumFractionDigits: 2,
        maximumFractionDigits: 2,
      });
    },
    formatCurrency(code) {
      const currency = this.currencies.find(c => c.code === code);
      return currency ? currency.name : code;
    },
  },
};
</script>

<style scoped>
.currency-converter {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f7f8fc;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  font-family: 'Arial', sans-serif;
}

h2 {
  color: #333;
  font-weight: 600;
  margin-bottom: 20px;
  font-size: 24px;
}

.input-group {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}

input[type="number"], select {
  padding: 15px; /* Aumenta el tamaño del padding para inputs y selects */
  font-size: 18px; /* Aumenta el tamaño de la fuente */
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 48%; /* Aumenta el ancho del select */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  transition: border-color 0.3s;
}

input[type="number"]:focus, select:focus {
  border-color: #007bbf;
  outline: none;
}

select {
  appearance: none; /* Elimina la apariencia predeterminada del navegador */
  background-color: white;
  cursor: pointer;
}

.select_value {
  padding: 10px;
}

button {
  margin-top: 20px;
  padding: 12px;
  width: 100%;
  background-color: #007bbf;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
}

button:hover {
  background-color: #005f8f;
  transform: translateY(-2px);
}

.result {
  margin-top: 20px;
}

h3 {
  color: #007bbf;
  font-weight: 500;
  font-size: 18px;
}

.to-text {
  margin: 0 5px;
  font-weight: 500;
  color: #333;
}
</style>
