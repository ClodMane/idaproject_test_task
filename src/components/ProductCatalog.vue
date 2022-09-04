<template>
  <div class="catalog">
    <div class="select">
      <ul class="select__options">
        <li
          class="select__option"
          data-select="option"
          data-value="по умолчанию"
          data-index="0"
        >
          По умолчанию
        </li>
        <li
          class="select__option"
          data-select="option"
          data-value="списком"
          data-index="1"
        >
          Списком
        </li>
      </ul>
    </div>
    <CatalogItem v-for="item in 9" :key="item" />
  </div>
</template>

<script>
import CatalogItem from "@/components/CatalogItem.vue";

export default {
  name: "ProductCatalog",
  props: {
    msg: String,
  },
  components: {
    CatalogItem,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
