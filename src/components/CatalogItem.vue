<template>
  <div :key="item" class="catalog-item item">
    <div class="delete-button">
      <button class="del-btn" @click="$emit('itemDelete', item.id)"></button>
    </div>
    <div class="item__image-wrapper">
      <img :src="item.link" alt="item image" class="item__image" />
    </div>
    <div class="item__body">
      <h3 class="item__head">{{ item.title }}</h3>
      <p class="item__text">{{ item.description }}</p>
    </div>
    <div class="item__footer">
      <h3 class="item__price">{{ item.price }} руб.</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "CatalogItem",
  props: {
    item: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.item {
  background-color: #fff;
  border-radius: 4px;
  position: relative;
  display: flex;
  flex-direction: column;

  &__text {
    font-size: 16px;
    line-height: 20.1px;
    color: rgba(63, 63, 63, 1);
    min-height: 80px;
  }

  &__body {
    padding: 0 0 0 16px;
    width: 300px;
    flex: 1 0 auto;
  }
  &__footer {
    flex-shrink: 0;
    padding: 0 16px;
  }

  &__head {
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
  &__image-wrapper {
    width: 100%;
    height: 200px;
    overflow: hidden;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
  }
  &__image {
    display: block;
    width: 100%;
    height: auto;
    object-fit: cover;
  }
}
.item:hover {
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.04), 0px 8px 12px rgba(0, 0, 0, 0.04);
  .del-btn {
    // display: block;
    transition: opacity 1s;
    opacity: 1;
    visibility: visible;
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
  // display: none;
  visibility: hidden;
}
</style>
