<template>
  <div id="product">
    <!-- Add your code here -->
    <div id="img-panel" class="border text-start" style="width: 65%"></div>
    <div id="info-panel" class="text-end ms-auto pe-5" style="width: 30%">
      <p class="text-start ps-1" style="border-left: 5px solid red">
        {{ product.product_offer_label }}
      </p>
      <p class="text-start border-bottom pb-3">
        {{ product.product_title }} | {{ product.product_colour }}
      </p>
      <div
        class="d-flex justify-content-between align-items-center border-bottom pb-1"
      >
        <table
          class="table table-sm table-borderless text-start"
          style="width: 10%"
        >
          <thead>
            <tr>
              <th scope="col">Original</th>
              <th scope="col">Now</th>
            </tr>
          </thead>
          <tbody class="text-start p-1">
            <tr>
              <td class="text-decoration-line-through">£{{ product.rrp }}</td>
              <td class="text-danger">£{{ product.selling_price }}</td>
            </tr>
          </tbody>
        </table>
        <p
          class="text-danger px-2"
          style="border-left: 2px solid red; border-right: 2px solid red"
        >
          Save
          {{ ((product.rrp - product.selling_price) / product.rrp) * 100 }}%
        </p>
      </div>
      <div id="alt-imgs" class="mt-3 pb-3 border-bottom">
        <ul class="list-group list-group-horizontal">
          <li
            class="list-group-item border-0 pe-0"
            v-for="(colours, index) in altColours"
            :key="index"
          >
            <img
              :src="colours.image"
              :width="75"
              :height="75"
              class="float-left"
            />
          </li>
        </ul>
      </div>
      <div id="sizes" class="mt-3 pb-3 border-bottom">
        <p class="text-start">Select size:</p>
        <ul class="list-group list-group-horizontal">
          <li
            class="list-group-item d-flex justify-content-center align-items-center"
            v-for="(size, index) in sizes"
            :key="index"
          >
            <p class="mb-0">{{ size }}</p>
          </li>
        </ul>
      </div>
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
      altColours: product.alternative_colours,
      sizes: product.product_size_labels,
      // Add any other data properties you need
    };
  },
  // Any Vue lifecycle hooks and custom JavaScript code can be added here
  mounted() {
    console.log(this.altColours);
  },
};
</script>

<style scoped lang="scss">
@import "../assets/css/poppins.css";
// Styling to be added here if needed. SASS is allowed if preferred
th,
td {
  font-weight: normal;
}
</style>
