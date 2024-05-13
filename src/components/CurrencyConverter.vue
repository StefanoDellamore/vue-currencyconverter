<script>
import axios from 'axios';

export default {
    data() {
        return {
            currencyOptions: [],
            selectedCurrency1: 'EUR',
            selectedCurrency2: 'USD',
            amount: 1,
            convertedAmount: null
        };
    },

    mounted() {
        this.fetchCurrencyOptions();
    },
    
    methods: {
        async fetchCurrencyOptions() {
            // Chiamata API per ottenere valuta
            try {
                const response = await axios.get('https://api.exchangerate-api.com/v4/latest/EUR');
                this.currencyOptions = Object.keys(response.data.rates);
                this.convertCurrencies();
            } catch (error) {
                console.error('Errore recupero', error);
            }
        },
        async convertCurrencies() {
            // Chiamata API per ottenere conversione
            try {
                const response = await axios.get (`https://api.exchangerate-api.com/v4/latest/${this.selectedCurrency1}`);
                const rate = response.data.rates[this.selectedCurrency2];
                this.convertedAmount = (this.amount * rate).toFixed(2);
            } catch (error) {
                console.error ('Errore conversione', error);
                this.convertedAmount = null;
            }
        },
        async fetchConvertedAmount() {
            // Chiamata API per ottenere conversione ad ogni imput utente
            try {
                const response = await axios.get(`https://api.exchangerate-api.com/v4/latest/${this.selectedCurrency1}`);
                const rate = response.data.rates[this.selectedCurrency2];
                const amountInEUR = this.convertedAmount / rate;
                this.amount = amountInEUR.toFixed(2);
            } catch (error) {
                console.error('Errore recupero importo', error);
                this.amount = null;
            }
        },
        
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
                class="currency-input"
                @input='convertCurrencies'/>
               

        <label class="label"></label>
        <select v-model="selectedCurrency1" class="currency-input">

            <option v-for="currency in currencyOptions" :key="currency" :value="currency">
                <span>{{ currency }}</span>
            </option>
            
        </select>


        <label for="convertedAmountInput" class="label"></label>
            <input
                type="number"
                id="convertedAmountInput"
                class="currency-input"
                v-model="convertedAmount"
                @input="fetchConvertedAmount"/>
                

        <label class="currency-label"></label>
        <select v-model="selectedCurrency2" class="currency-input">
            <option v-for="currency in currencyOptions" :key="currency" :value="currency">
                {{ currency }}
            </option>
        </select>
        
    </div>

</template>

<style lang="scss" scoped>
</style>