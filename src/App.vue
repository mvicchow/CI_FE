<template>
  <ProductController />
</template>

<script>
import ProductController from './components/ProductController.vue';

export default {
  name: 'App',
    data() {
        return {
            womenPrimaryColor: "#720060",
            womenSecondaryColor: "#FDE2FF",
            menPrimaryColor: "#002772",
            menSecondaryColor: "#D6E6FF",
            otherPrimaryColor: "rgb(154, 164, 11)",
            otherSecondaryColor: "rgb(214, 229, 15)"
        };
    },
  components: {
    ProductController
  }
}
</script>

<style>
:root {
  font-family: 'Inter';
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: justify;
  display: flex;
  justify-content: center;
}

.women-themed-primary {
    color: v-bind(womenPrimaryColor);
}

.women-themed-secondary {
    color: v-bind(womenSecondaryColor);
}

.men-themed-primary {
    color: v-bind(menPrimaryColor);
}

.men-themed-secondary {
    color: v-bind(menSecondaryColor);
}

.other-themed-primary {
    color: v-bind(otherPrimaryColor);
}

.other-themed-secondary {
    color: v-bind(otherSecondaryColor);
}

</style>
