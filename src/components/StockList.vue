<template>
    <div>
        <h1>StockList</h1>
        <table class="table">
            <thead>
                <td>Name</td>
                <td>Price</td>
            </thead>
            <tbody>
                <tr v-for="stock in stocks" :key="stock.name">
                    <td>{{ stock.name }}</td>
                    <td>
                        <b :class="{ 'green': stock.price > stock.previousPrice, 'red': stock.price < stock.previousPrice }">{{ stock.currency }} {{ stock.price.toFixed(2) }}</b>
                    </td>
                </tr>
            </tbody>
        </table>
        <button @click="updatePrices()">Update</button>
    </div>
</template>

<script>
export default {
    name: "StockList",
    data() {
        return {
            stocks: [
                { name: "BMW", price: 61.05, previousPrice: 0, currency: "€" },
                { name: "Caterpillar", price: 146.49, previousPrice: 0, currency: "$" },
                { name: "AMD", price: 76.5, previousPrice: 0, currency: "$" },
                { name: "Tesla", price: 4.583, previousPrice: 0, currency: "$" },
            ],
            portfolio: [],
        }
    },
    methods: {
        updatePrices() {
            this.stocks.forEach((stock) => {
                stock.previousPrice = stock.price;
                stock.price += (Math.random() - 0.5) * 2;
                if (stock.price < 0) {
                    stock.price = 0;
                }
            });
        },
    },
    mounted() {
        setInterval(() => {
            this.updatePrices()
        }, 1000)
    }
}
</script>

<style scoped>
td {
    border: solid white 1px;
}

.red {
    color: red;
}

.green {
    color: greenyellow;
}
</style>