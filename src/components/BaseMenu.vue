<template>
  <div class="main-form__wrapper">
    <h2 class="menu-heading">Добавление товара</h2>
    <form action="" class="main-form" @submit.prevent="submitHandler">
      <div class="main-from-item">
        <label for="name">Наименование товара </label>
        <input
          v-model="v$.title.$model"
          :class="{
            invalid: v$.title.$dirty,
          }"
          id="name"
          type="text"
          name="name"
          placeholder="Введите наименование товара"
          required
          @blur="inputHandler('title')"
        />
        <small
          class="helper-text invalid"
          v-if="v$.title.$dirty && v$.title.$errors.length > 0"
        >
          Поле является обязательным</small
        >
      </div>
      <div class="main-from-item">
        <label for="description">Описание товара </label>
        <textarea
          v-model="description"
          placeholder="Введите описание"
          name=""
          id="description"
          cols="10"
          rows="5"
        />
      </div>
      <div class="main-from-item">
        <label for="url">Ссылка на изображение товара </label>
        <input
          v-model="v$.link.$model"
          :class="{
            invalid: v$.link.$dirty,
          }"
          type="url"
          name="link"
          placeholder="Введите ссылку"
          required
          @blur="inputHandler('link')"
          id="url"
        />
        <small
          v-if="v$.link.$dirty && v$.link.required.$invalid"
          class="helper-text invalid"
        >
          Поле является обязательным
        </small>
        <small
          class="helper-text__link invalid"
          v-else-if="v$.link.$dirty && v$.link.url.$invalid"
        >
          Введите ссылку</small
        >
      </div>
      <div class="main-from-item">
        <label for="price">Цена товара </label>
        <input
          v-model="v$.price.$model"
          :class="{
            invalid: v$.price.$dirty,
          }"
          type="number"
          name="price"
          placeholder="Введите цену"
          required
          @blur="inputHandler('price')"
          id="price"
        />
        <small
          class="helper-text invalid"
          v-if="v$.price.$dirty && v$.price.$errors.length > 0"
        >
          Поле является обязательным</small
        >
      </div>
      <button class="form-button" type="submit">Добавить товар</button>
    </form>
  </div>
</template>

<script>
import useVuelidate from "@vuelidate/core";
import { required, url } from "@vuelidate/validators";
export default {
  setup() {
    return { v$: useVuelidate() };
  },
  name: "BaseMenu",
  props: {
    msg: String,
  },
  data() {
    return {
      title: "",
      description: "",
      link: "",
      price: "",
    };
  },
  validations() {
    return {
      title: { required }, // Matches this.firstName
      link: { required, url }, // Matches this.lastName
      price: { required },
    };
  },
  methods: {
    async submitHandler() {
      const result = await this.v$.$validate();
      if (!result) {
        console.log("fale");
      } else {
        console.log("wine");
      }
    },
    inputHandler(input) {
      if (!this.v$[input].$model) {
        this.v$[input].$touch();
      }
    },
  },
};
</script>

<style lang="scss">
.main-form {
  width: 332px;
  height: auto;
  min-height: 440px;
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
  margin-bottom: 4px;
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
  line-height: 15.08px;
  padding-left: 16px;
}
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

textarea {
  width: 100%;
  height: 108px;
  border: none;
  border-radius: 4px;
  resize: none;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  color: #b4b4b4;
  font-family: "Source Sans Pro", sans-serif;
  font-size: 12px;
  line-height: 15.08px;
  padding: 10px 0 0 16px;
  background: #fffefb;
}

.helper-text {
  color: rgba(255, 132, 132, 1);
  font-size: 8px;
  line-height: 10.06px;
  margin: 4px 0 0 0;
  &__link {
    color: rgba(255, 132, 132, 1);
    font-size: 8px;
    line-height: 10.06px;
    margin: 4px 0 0 0;
  }
}
</style>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
