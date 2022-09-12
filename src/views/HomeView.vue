<template>
  <div>
    <BannerSecVue />
    <ProductsSecVue />
  </div>
</template>

<script>
import BannerSecVue from "@/components/BannerSec.vue";
import ProductsSecVue from "@/components/ProductsSec.vue";

export default {
  name: "App",
  components: {
    BannerSecVue,
    ProductsSecVue,
  },
};
</script>
