<template>
  <div class="home">
    <BaseMenu />
    <ProductCatalog />
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
