<template>
    <div>
        <span class="bullet" v-for="n in [1, 2, 3, 4, 5]" :key="n" :class="[fillBullet(n), this.color]"></span>
    </div>
</template>

<script>
export default {
    name: "RatingBullet",
    props: ["rate", "color"],

    data() {
        return {
            bulletToFill: Math.round(this.rate)
        };
    },
    methods: {
        fillBullet(x) {
            return (x <= this.bulletToFill) ? "bullet-filled" : "bullet-empty";
        }
    }
}
</script>

<style>
.bullet {
    display: inline-block;
    width: 10px;
    height: 10px;
    border: 1px;
    border-style: solid;
    border-radius: 50%;
    margin-right: 5px;
}

.bullet-filled {
    background-color: currentColor;
}

.bullet-empty {
    background-color: wheat;
}

</style>
