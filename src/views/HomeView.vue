<template>
  <div class="home-wrapper">
    <div class="home">
      <BaseMenu />
      <ProductCatalog />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import BaseMenu from "@/components/BaseMenu.vue";
import ProductCatalog from "@/components/ProductCatalog.vue";

export default {
  name: "HomeView",
  components: {
    BaseMenu,
    ProductCatalog,
  },
};
</script>

<style scoped lang="scss">
.home {
  display: flex;
  flex-direction: row;
  gap: 16px;
  max-width: 1376px;
  margin: 0 auto;
}
</style>
