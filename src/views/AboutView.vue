<template>
  <div class="about">
    <!-- <h1>Your total order : {{ dataArray.length }}</h1> -->
    <h1>
      {{
        dataArray.length
          ? `Your Total order is : ${dataArray.length}`
          : "There is no product ☢"
      }}
    </h1>
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
    <div>
      <div>
        <div>
          <div class="items" v-for="item in dataArray" v-bind:key="item.index">
            <p class="">
              Name: {{ item.title }}
              <span class="spacebetwwen">Price: {{ item.price }}</span>
              <span>Quantity: {{ item.quantity }}</span>
            </p>
            <!-- <ProductCard :product="item" /> -->
          </div>
        </div>
        <div>
          <hr />
          <p>Sub total : {{ subTotalPrice }}</p>
          <p>Vat: 20%</p>
          <hr />
          <p>Total: {{ total }}</p>
        </div>
        <!-- <ProductCard :product="item" /> -->
        <button>Dowonload</button>
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
      perPriceName: "",
      perPrice: 0,
      subTotalPrice: 0,
      total: 0,
    };
  },
  methods: {
    xbutton(id) {
      this.dataArray.splice(id, 1);
    },
    /* invoice() {
      this.dataArray.map((d) => {
        this.perPrice = d.price * d.quantity;
        this.subTotalPrice = this.subTotalPrice + this.perPrice;
        this.total = (this.subTotalPrice + this.subTotalPrice * 0.2).toFixed(2);
      });
    }, */
  },
  mounted() {
    this.dataArray.map((d) => {
      this.perPrice = d.price * d.quantity;
      this.subTotalPrice = this.subTotalPrice + this.perPrice;
      this.total = (this.subTotalPrice + this.subTotalPrice * 0.2).toFixed(2);
    });
    // invoice()
  },
};
</script>
