<template>
  <div id="product" class="d-flex">
    <!-- Add your code here -->
    <div
      id="img-panel"
      class="border-0 text-start ms-5"
      style="width: 65%; flex: 2"
    >
      <div class="row g-0 border-bottom pb-1 mb-3">
        <div class="col-6" v-for="(image, index) in gallery" :key="index">
          <img
            :src="image.image"
            :alt="image.alt"
            style="width: 95%; height: auto"
            class="img-fluid pb-3"
          />
        </div>
      </div>
    </div>
    <div
      id="info-panel"
      class="text-end ms-auto pe-5"
      style="width: 30%; flex: 1"
    >
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
              <td class="text-decoration-line-through">
                £{{ product.rrp }}.00
              </td>
              <td class="text-danger">£{{ product.selling_price }}.00</td>
            </tr>
          </tbody>
        </table>
        <p
          class="text-danger px-2"
          style="border-left: 2px solid red; border-right: 2px solid red"
        >
          Save
          {{ priceReduction }}%
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
              :alt="colours.alt_text"
              class="float-left"
            />
          </li>
        </ul>
      </div>
      <div id="sizes" class="mt-3 pb-3 border-bottom">
        <p class="text-start">Select size:</p>
        <div class="container">
          <div class="row">
            <div class="col" v-for="(size, index) in sizes" key="index">
              <input
                type="radio"
                class="btn-check"
                name="options"
                :id="`option${index + 1}`"
                autocomplete="off"
                checked
                :value="size"
                v-model="selectedSize"
              />
              <label
                class="btn btn-outline-dark rounded-0 custom-border"
                :for="`option${index + 1}`"
                >{{ size }}</label
              >

              <!-- <button
                class="btn btn-outline-dark rounded-0 custom-border"
                data-bs-toggle="button"
                aria-pressed="false"
                autocomplete="off"
              >
                {{ size }}
              </button> -->
            </div>
          </div>
        </div>
        <!-- <ul class="list-group list-group-horizontal">
          <li
            class="list-group-item border-0"
            v-for="(size, index) in sizes"
            :key="index"
            style="margin-right: -15px"
          >
            <p class="mb-0 custom-border">{{ size }}</p>
          </li>
        </ul> -->
      </div>
      <div id="addbag-button" class="pb-3">
        <button
          type="button"
          class="btn rounded-pill btn-dark mt-3"
          style="width: 100%"
          data-bs-toggle="modal"
          data-bs-target="#addToBagModal"
        >
          Add To Bag
        </button>
      </div>
      <div id="description" class="text-start">
        <p>Description</p>
        <p>{{ product.product_description }}</p>
        <p v-html="product.product_bulletpoints"></p>
        <p>Product code: {{ product.product_sku }}</p>
      </div>
    </div>
    <div
      class="modal fade"
      id="addToBagModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog">
        <div class="modal-content rounded-0">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="item-title">Item Added!</h1>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div
            class="modal-body d-flex align-items-center justify-content-between"
          >
            <img
              :src="gallery[0].image"
              :width="75"
              :height="75"
              :alt="gallery[0].alt"
              class="float-left"
            />
            <p class="text-end">
              {{ product.product_title }} <br />
              You have selected size:
              {{ selectedSize }}
            </p>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary rounded-pill"
              data-bs-dismiss="modal"
            >
              Close
            </button>
            <button type="button" class="btn btn-dark rounded-pill">
              Go To Bag
            </button>
          </div>
        </div>
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
      gallery: product.media_gallery,
      priceReduction:
        ((product.rrp - product.selling_price) / product.rrp) * 100,
      selectedSize: null,
      // Add any other data properties you need
    };
  },
  // Any Vue lifecycle hooks and custom JavaScript code can be added here
  mounted() {
    console.log(this.selectedSize);
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
.custom-border {
  width: 65px;
  height: 65px;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: -15px;
  margin-top: -15px;
}
</style>
