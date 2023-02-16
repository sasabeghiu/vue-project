<template>
    <div class="col-md-4 mt-4">
        <div class="card">
            <div class="card-body">
                <td>{{ name }}</td>
                <span :class="{ down: price < previousPrice, up: price > previousPrice }">
                    {{ currency }} {{ price.toFixed(4) }}</span>
            </div>
            <input class="form-control" type="number" v-model="amount">
            <button class="btn btn-primary" @click="$emit('buy', name, amount)">Buy</button>
        </div>
</div>
</template>

<script>
export default {
    name: "StockItem",
    props: {
        name: String,
        currency: String,
        price: Number,
        previousPrice: Number,
    },
    data() {
        return {
            amount: 0
        }
    }
};
</script>

<style scoped>
.up {
    color: green;
}

.down {
    color: red;
}
</style>