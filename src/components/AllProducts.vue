<template>
  <div>
    <div class="itemcard">
      <div class="items" v-for="item in products" v-bind:key="item.id">
        <h2>Name: {{ item.title }}</h2>
        <img class="image" :src="item.image" alt="" />
        <p>Price: {{ item.price }}</p>
        <p>Rating: {{ item.rating.rate }}</p>
        <p>Count: {{ item.rating.count }}</p>
        <button @click="addToCars(item)" class="">Add to card</button>
        <!-- <ProductCard :product="item" /> -->
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "AllProducts",
  props: {
    products: Array,
  },
  data() {
    return {
      cartData: [],
    };
  },
  methods: {
    addToCars(item) {
      let isExsit = this.cartData.find((el) => {
        return el.title == item.title;
      });
      if (isExsit) {
        isExsit.quantity += 1;
        return;
      } else {
        let cartItem = {
          title: item.title,
          price: item.price,
          quantity: 1,
        };
        this.cartData.push(cartItem);
      }
      this.$store.state.carts = this.cartData;
      /* {{ $store.state.name }} */
    },
  },
};
</script>
<style lang="scss">
.itemcard {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  .items {
    background-color: rgb(2, 116, 8);
    margin: 10px;
    padding: 5px 0;
    text-align: center;
    border-radius: 10px;
  }
  img {
    width: 100px;
    max-width: 100%;
  }
}
</style>
