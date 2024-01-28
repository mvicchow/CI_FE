<template>
    <div class="product-image-wrap">
        <img class="product-image" :src="this.data['image']" alt="Failed to load image">
    </div>
    <div class="product-detail">
        <div class="product-title" :class="getPrimaryTheme()">
            {{ this.data['title'] }}
        </div>
        <div class="product-data">
            <div class="product-category">
                {{ this.data['category'] }}
            </div>


            <div class="product-rating">
                {{ this.data['rating']?.['rate'] }} / 5.0
                <RatingBullet v-bind:rate="this.data['rating']?.['rate']" v-bind:class="getPrimaryTheme()" />
            </div>
        </div>
        <hr>
        <div class="product-description">
            {{ this.data['description'] }}
        </div>
        <hr>
        <div class="product-price" :class="getPrimaryTheme()">
            $ {{ this.data['price'] }}
        </div>
        <div class="product-action" :class="getPrimaryTheme()">
            <button class="buy-button">
                <p>BUY NOW</p>
            </button>
            <button class="next-product-button" @click="$emit('nextData')">
                NEXT PRODUCT
            </button>
        </div>
    </div>
    <div class="pembantu" :class="getSecondaryTheme()"></div>
</template>

<script>
import RatingBullet from './RatingBullet.vue';

export default {
    name: 'ProductCard',
    data() {
        return {
            imageLoaded: false,
        };
    },
    emits: ['nextData'],
    props: ['data', 'nextData'],
    methods: {
        getPrimaryTheme() {
            if (this.data['category'] == "men's clothing")
                return 'men-themed-primary';
            if (this.data['category'] == "women's clothing")
                return 'women-themed-primary';
            else return 'other-themed-primary';
        },
        getSecondaryTheme() {
            if (this.data['category'] == "men's clothing")
                return 'men-themed-secondary';
            if (this.data['category'] == "women's clothing")
                return 'women-themed-secondary';
            else return 'other-themed-secondary'
        },
        addThemeToBody() {
            const body = document.body;
            const pembantu = document.getElementsByClassName("pembantu");

            // body.style.backgroundColor = `linear-gradient(to right, ${getComputedStyle(pembantu[0]).color} 50%, blue 50%)`;
            // body.style.backgroundColor = 'linear-gradient(white 0%, red 100%)'
            body.style.backgroundColor = getComputedStyle(pembantu[0]).color;
            // console.log(getComputedStyle(body).backgroundColor)
            // console.log(getComputedStyle(pembantu[0]).font)
        }
    },
    components: { RatingBullet },
    mounted() {
        this.addThemeToBody();
    },
}
</script>


<style>
hr {
    border: 0;
    clear: both;
    display: block;
    width: 100%;
    background-color: rgb(35, 35, 35);
    height: 1px;
}

.product-action {
    display: flex;
    justify-content: space-between;
}

button {
    color: v-bind(getPrimaryTheme);
    width: 20vw;
    font-size: 16px;
    border-radius: 8px;
    border-style: solid;
    border-color: currentColor;
}

.next-product-button {
    background-color: white;
}

.buy-button {
    background-color: currentColor;
}

.buy-button p {
    color: white;
}


.product-image-wrap {
    width: 30%;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.product-image {
    width: 100%;
}

.product-title {
    font-weight: bolder;
    font-size: x-large;
}

.product-detail {
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    width: 70%;
    /* margin: 30px; */
    padding: 20px;
}


.product-rating {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 15vw;
}

.product-data {
    color: #3f3f3f;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.product-description {

    color: #1e1e1e;
}


.product-price {
    font-size: larger;
    font-weight: bold;
}
</style>
