<template>
  <div class="products">
    <h1 class="title">Choice your best products</h1>
    <div class="body-container">
      <div class="shorting">
        <div class="stiky">
          <div class="shortestList">
            <button @click="shortPrice(50)">Lowest price</button>
            <br />
            <button @click="shortPrice(100)">Heightest price</button>
            <br />
            <button @click="shorrate(3.8)">Best rating</button>
            <br />
            <button @click="shorrate(3)">lowest rating</button>
            <br />
            <button @click="showAll">Show all</button>
          </div>
          <h2 class="itemcart">Cart - ({{ $store.state.carts.length }})</h2>
        </div>
      </div>
      <div>
        <AllProductsVue :products="shortedData"></AllProductsVue>
      </div>
    </div>
  </div>
</template>
<script>
import AllProductsVue from "./AllProducts.vue";
export default {
  name: "ProductsSec",
  components: {
    AllProductsVue,
  },
  data() {
    return {
      produtc: [],
      shortedData: [],
    };
  },
  methods: {
    shortPrice(value) {
      const valus = this.produtc;
      const result = valus.filter((element) => element?.price <= value);
      this.shortedData = [...result];
    },
    shorrate(rating) {
      const valus = this.produtc;
      const result = valus.filter((element) => element?.rating?.rate > rating);
      this.shortedData = [...result];
    },
    showAll() {
      this.shortedData = [...this.produtc];
    },
    getData() {
      this.axios.get("https://fakestoreapi.com/products").then((response) => {
        this.produtc = response.data;
        this.shortedData = [...this.produtc];
      });
    },
  },
  mounted() {
    this.getData();
  },
};
</script>
<style lang="scss">
.products {
  padding: 10px 20px;
}
</style>
