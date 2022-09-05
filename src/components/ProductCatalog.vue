<template>
  <div class="catalog__wrapper-head">
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
          style="display: none"
        >
          По цене
        </li>
        <li
          class="select__option"
          data-select="option"
          data-value="списком"
          data-index="1"
          style="display: none"
        >
          По наименованию
        </li>
      </ul>
    </div>
    <div class="catalog__wrapper">
      <div class="catalog">
        <CatalogItem v-for="item in 9" :key="item" />
      </div>
    </div>
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
<style scoped lang="scss">
.catalog {
  display: grid;
  grid-template-columns: repeat(3, 332px);
  justify-content: space-between;
  grid-row-gap: 5px;
  grid-column-gap: 5px;
  gap: 16px;
}
.select {
  &__options {
    list-style-type: none;
    color: #b4b4b4;
    font-size: 12px;
    line-height: 15px;
    background-color: #fff;
    width: 122px;
    height: 36px;
    border-radius: 4px;
  }
}
</style>
