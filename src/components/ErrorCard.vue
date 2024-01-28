<template>
    <div class="errorCardWrapper">
        <p>{{ this.message }}</p>
            <button class="next-product-button" @click="$emit('nextData')">
                <p>NEXT PRODUCT</p>
            </button>
    </div>

</template>

<script>
    export default{
        name: "ErrorCard",
        emits: ['nextData'],
        props: ["message"],
        methods:
     {
        changeBodyColor() {
            const body = document.body;
            body.style.backgroundColor = 'gray';
        }
    },
    mounted() {
        this.changeBodyColor();
    }

    }
</script>


<style scoped>

.errorCardWrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: center;
    justify-content: space-around;
    width: 100%;
}

</style>
