<template>
  <div id="product">
    <!-- Add your code here -->
    <div id="img-panel" class="border text-start" style="width: 65%"></div>
    <div
      id="info-panel"
      class="text-end ms-auto border-bottom"
      style="width: 30%"
    >
      <p class="text-start ps-1" style="border-left: 5px solid red">
        {{ product.product_offer_label }}
      </p>
      <p class="text-start">
        {{ product.product_title }} | {{ product.product_colour }}
      </p>
    </div>
  </div>
</template>

<script>
import product from "../components/data/product.json";

export default {
  name: "ProductPage",
  data() {
    return {
      product: product,
      // Add any other data properties you need
    };
  },
  // Any Vue lifecycle hooks and custom JavaScript code can be added here
  mounted() {
    console.log(product.media_gallery);
  },
};
</script>

<style scoped lang="scss">
@import "../assets/css/poppins.css";
// Styling to be added here if needed. SASS is allowed if preferred
</style>
