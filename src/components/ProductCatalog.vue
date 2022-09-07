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
          <div>
            <svg
              width="8"
              height="6"
              viewBox="0 0 8 6"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M7.48532 1.24264L4.24268 4.48528L1.00003 1.24264"
                stroke="#B4B4B4"
              />
            </svg>
          </div>
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
        <CatalogItem
          v-for="item in catalogItems"
          :key="item"
          :item="item"
          @itemDelete="deleteItem"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CatalogItem from "@/components/CatalogItem.vue";

export default {
  name: "ProductCatalog",
  components: {
    CatalogItem,
  },
  props: {
    newItem: Object,
  },
  data() {
    return {
      catalogItems: [
        {
          id: 0,
          link: "https://nuxtjs-goodss.vercel.app/product-photo.jpg",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 1,
          link: "https://nuxtjs-goodss.vercel.app/product-photo.jpg",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
        {
          id: 2,
          link: "https://nuxtjs-goodss.vercel.app/product-photo.jpg",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10000",
        },
      ],
    };
  },
  watch: {
    newItem(newVal) {
      let item = newVal;
      if (newVal) {
        item.id = this.catalogItems.length;
        this.catalogItems.unshift(item);
      }
    },
  },
  methods: {
    deleteItem(id) {
      this.catalogItems = this.catalogItems.filter((item) => item.id != id);
    },
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
  display: flex;
  justify-content: flex-end;
  margin-top: 11px;

  &__options {
    list-style-type: none;
    color: #b4b4b4;
    font-size: 12px;
    line-height: 15px;
    background-color: #fff;
    width: 122px;
    height: 36px;
    border-radius: 4px;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 0;

    li {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 5px;
    }
  }
}
</style>
