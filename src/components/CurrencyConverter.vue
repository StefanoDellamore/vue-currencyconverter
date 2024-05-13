<script>
export default {
    data() {
        return {

        };
    },
    methods: {

    }
}
</script>

<template>

    <div>
        <label for="amountInput" class="label"></label>
            <input type="number" id="amountInput">

        <label class="label"></label>
        <select name="currency" id="currency">
            <option value="currency">eur</option>
            <option value="currency">usd</option>
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