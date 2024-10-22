<template>
  <div class="app">
    <CurrencyConverter />
  </div>
</template>

<script>
import CurrencyConverter from './components/CurrencyConverter.vue';

export default {
  name: 'App',
  components: {
    CurrencyConverter,
  },
};
</script>

<style src="./styles.css"></style>
