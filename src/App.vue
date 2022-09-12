<template>
  <div id="app">
    <div>
      <NavBarVue />
    </div>
    <div>
      <router-view />
    </div>
  </div>
</template>

<script>
import NavBarVue from "./components/NavBar.vue";

export default {
  name: "App",
  components: {
    NavBarVue,
  },
};
</script>
