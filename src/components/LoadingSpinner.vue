<template>
    <div class="loader-wrapper">
        <div class="loader"></div>
    </div>
</template>

<script>
export default {
    name: "LoadingSpinner",
}
</script>

<style scoped>

.loader-wrapper{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}

.loader {
    border: 16px solid #f3f3f3;
    /* Light grey */
    border-top: 16px solid #7b7b7c;
    /* Blue */
    border-radius: 50%;
    width: 120px;
    height: 120px;
    animation: spin 2s linear infinite;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
</style>
