<template>
  <div :key="item" class="catalog-item item">
    <div class="delete-button"><button class="del-btn"></button></div>
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
<style scoped lang="scss">
.item {
  background-color: #fff;
  border-radius: 4px;
  position: relative;

  &__text {
    font-size: 16px;
    line-height: 20.1px;
    color: rgba(63, 63, 63, 1);
  }

  &__body {
    padding: 0 0 0 16px;
    width: 300px;
  }

  &__head {
    padding: 0 0 0 16px;
    color: rgba(63, 63, 63, 1);
    font-size: 20px;
    line-height: 25.14px;
    font-weight: 600;
  }

  &__price {
    font-size: 24px;
    font-weight: 600;
    line-height: 30.17px;
    color: rgba(63, 63, 63, 1);
  }
}
.del-btn {
  height: 32px;
  width: 32px;
  background-color: rgba(255, 132, 132, 1);
  background: url(../assets/images/icons/delete1.png) no-repeat center
    rgba(255, 132, 132, 1);
  border: none;
  border-radius: 10px;
  position: absolute;
  right: -8px;
  top: -8px;
}
</style>
