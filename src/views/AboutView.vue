<template>
  <div class="about">
    <h1>Your total order : {{ $store.state.carts.length }}</h1>
    <div>
      <div class="items" v-for="item in dataArray" v-bind:key="item.index">
        <h2 class="bg-color">
          Name: {{ item.title }}
          <span class="spacebetwwen">Price: {{ item.price }}</span>
          <span>Quantity: {{ item.quantity }}</span>
          <button
            @click="xbutton($store.state.carts.indexOf(item))"
            class="xbutton"
          >
            X
          </button>
        </h2>
        <!-- <ProductCard :product="item" /> -->
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "AboutView",
  data() {
    return {
      dataArray: this.$store.state.carts,
    };
  },
  methods: {
    xbutton(id) {
      this.$store.state.carts.splice(id, 1);
    },
  },
};
</script>
