<template>
  <div class="home-wrapper">
    <div class="home">
      <BaseMenu @createNewObject="createNewObject" />
      <ProductCatalog :new-item="newObject" />
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
  data() {
    return {
      newObject: {},
    };
  },
  methods: {
    createNewObject(form) {
      this.newObject = form;
    },
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
