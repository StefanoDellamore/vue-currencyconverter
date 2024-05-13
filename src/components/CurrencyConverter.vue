<script>
import axios from 'axios';

export default {
    data() {
        return {
            currencyOptions: [],
            selectedCurrency1: 'EUR',
            selectedCurrency2: 'USD',
            amount: 1
        };
    },

    mounted() {
        this.fetchCurrencyOptions();
    },
    
    methods: {
        async fetchCurrencyOptions() {
            // Chiamata API per ottenere la valuta
            try {
                const response = await axios.get('https://api.exchangerate-api.com/v4/latest/EUR');
                this.currencyOptions = Object.keys(response.data.rates);
                this.convertCurrencies();
            } catch (error) {
                console.error('Error fetching currency options:', error);
            }
        }
    }
}
</script>

<template>

    <div>
        <label for="amountInput" class="currency-label"></label>
            <input
                type="number"
                v-model.number="amount"
                id="amountInput"
                class="currency-input">

        <label class="label"></label>
        <select v-model="selectedCurrency1" class="currency-input">

            <option v-for="currency in currencyOptions" :key="currency" :value="currency">
                <span>{{ currency }}</span>
            </option>
            
        </select>


        <label for="convertedAmount" class="label"></label>
            <input type="number" id="convertedAmount">

        <label class="label"></label>
        <select name="currency" id="currency">
            <option value="currency">eur</option>
            <option value="currency">usd</option>
        </select>
        
    </div>

</template>

<style lang="scss" scoped>
</style>