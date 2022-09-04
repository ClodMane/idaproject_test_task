<template>
  <div :key="item" class="catalog-item item">
    <div class="item__image-wrapper">
      <img
        src="@/assets/images/catalog/Rectangle30.png"
        alt="item image"
        class="frame"
      />
    </div>
    <h3 class="item__head">Наименование товара</h3>
    <div class="item__body">
      <p class="item__text">
        Довольно-таки интересное описание товара в несколько строк.
        Довольно-таки интересное описание товара в несколько строк
      </p>
      <h3 class="item__price">10 000 руб.</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "CatalogItem",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
