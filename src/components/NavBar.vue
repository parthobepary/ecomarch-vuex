<template>
  <div class="navbar">
    <div>
      <h1>Phone <span>Buzz</span></h1>
    </div>
    <nav class="navitem">
      <router-link class="item" to="/">Home</router-link>
      <router-link class="item" to="/about">About</router-link>
      <router-link class="item" to="/about">Card</router-link>
      <router-link class="item" to="/about">Contact</router-link>
    </nav>
  </div>
</template>
<script>
export default {
  name: "NavBar",
};
</script>
