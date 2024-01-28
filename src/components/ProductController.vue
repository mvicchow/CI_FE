<template>
    <div class="card-wrapper">
        <LoadingSpinner v-if="loading"/>
        <ErrorCard v-else-if="dataUnavailable" v-bind:message="this.data" @nextData="nextData"/>
        <ProductCard v-else v-bind:data="data" @nextData="nextData"/>
    </div>
</template>

<script>
import LoadingSpinner from './LoadingSpinner.vue';
import ProductCard from './ProductCard.vue';
import ErrorCard from './ErrorCard.vue';

export default {
    name: 'ProductController',
    components: {
        LoadingSpinner,
        ProductCard,
        ErrorCard
    },
    data() {
        return {
            data: {},
            loading: true,
            index: 1,
            dataUnavailable: false,
        };
    },
    mounted() {
        this.fetchData();
    },
    methods: {
        async fetchData() {
            console.log("index :", this.index);
            try {
                const response = await fetch(`https://fakestoreapi.com/products/${this.index}`);
                this.data = await response.json();
                this.loading = false;
            } catch (error) {
                this.data = "Hold on tight, an error has just occured, please contact administrator!";
                console.error('Error fetching data:', error);
                this.loading = false;
                this.dataUnavailable= true;
            }
            // console.log(this.dataUnavailable);
        },
        nextData() {
            this.loading = true;
            this.dataUnavailable= false,
            // this.index++;
            this.index == 20 ? this.index = 1 : this.index++;
            this.fetchData();
        },
    },
};
</script>

<style>

.card-wrapper {
    position: absolute;
    display: flex;
    justify-content: space-between;
    min-height: 60vh;
    width: 80vw;
    margin: 20px;
    padding: 20px;
    background-color: white;
    border-radius: 15px;
    box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
}
</style>
