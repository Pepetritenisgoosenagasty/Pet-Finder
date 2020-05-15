<template>
  <div id="app">
    <div
      id="nav"
      class="h-16 w-full py-4 text-xl font-mono text-green-500 text-center"
    >
      <router-link to="/" class="text-xl font-mono text-green-500"
        >Home</router-link
      >
      |
      <router-link to="/cats" class="text-xl font-mono text-green-500"
        >Cats</router-link
      >
      |
      <router-link to="/dogs" class="text-xl font-mono text-green-500"
        >Dogs</router-link
      >
      <!-- |
      <router-link to="/pets" class="text-xl font-mono text-green-500"
        >Pets</router-link -->
      <!-- > -->
    </div>
    <router-view />
  </div>
</template>
<script>
import "@/assets/css/main.css";
export default {
  name: "App"
};
</script>
<style lang="scss">
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    &.router-link-exact-active {
      color: teal;
    }
  }
}
</style>
