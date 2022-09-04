<template>
  <h2 class="menu-heading">Добавление товара</h2>
  <form action="" class="main-form">
    <div class="main-from-item">
      <label for="name">Наименование товара </label>
      <input
        id="name"
        type="text"
        name="name"
        placeholder="Введите наименование товара"
        required
      />
    </div>
    <div class="main-from-item">
      <label for="description">Описание товара </label>
      <textarea name="" id="description" cols="10" rows="5">
Введите описание товара</textarea
      >
    </div>
    <div class="main-from-item">
      <label for="url">Ссылка на изображение товара </label>
      <input
        type="url"
        name="link"
        placeholder="Введите ссылку"
        required
        id="url"
      />
    </div>
    <div class="main-from-item">
      <label for="price">Цена товара </label>
      <input
        type="number"
        name="price"
        placeholder="Введите цену"
        required
        id="price"
      />
    </div>
    <button class="form-button">Добавить товар</button>
  </form>
</template>

<script>
export default {
  name: "BaseMenu",
  props: {
    msg: String,
  },
};
</script>

<style lang="scss">
.main-form {
  width: 332px;
  height: 440px;
  border: none;
  border-radius: 4px;
  font-size: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  background: #fffefb;
  padding: 24px;
  gap: 16px;
}
.main-from-item {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.form-button {
  background-color: #eeeeee;
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 10px;
  color: #b4b4b4;
}

label {
  font-size: 10px;
  color: #49485e;
}
input {
  width: 100%;
  height: 36px;
  border-radius: 4px;
  border: none;
  background: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
}
input::-webkit-input-placeholder {
  color: #b4b4b4;
  font-size: 12px;
}

textarea {
  width: 100%;
  height: 108px;
  border: none;
  border-radius: 4px;
  resize: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  color: #b4b4b4;
}
</style>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
