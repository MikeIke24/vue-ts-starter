<template>
<div class="basket-container">
    <div>Is loading = {{isLoading}}</div>
    <div>Number of items = {{numberOfItems}}</div>
    <div> items = {{items}}</div>
    <button v-on:click="addToBasket('test item', 5)">Add item</button>
</div>
</template>

<script lang="ts">
    import Vue from "vue";
    import Component from "vue-class-component";
    import basket from "../store/basket";

    @Component({})
    export default class BasketDisplay extends Vue {
        get isLoading() { return basket.state.isLoading }
        get items() { return basket.items }
        get numberOfItems() { return basket.numberOfItems }

        restoreSavedBasket()
        {
            basket.dispatchRestoreSavedBasket()
        }

        addToBasket(productId: string, quantity: number = 1)
        {
            basket.commitAppendItem({ productId, quantity })
        }
    }
</script>

<style>

</style>

