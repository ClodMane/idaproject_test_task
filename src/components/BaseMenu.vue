<template>
  <div class="main-form__wrapper">
    <h2 class="menu-heading">Добавление товара</h2>
    <form action="" class="main-form" @submit.prevent="submitHandler">
      <div class="main-from-item">
        <label for="name">Наименование товара </label>
        <input
          v-model="v$.title.$model"
          :class="{
            invalid: v$.title.$dirty && v$.title.$errors.length > 0,
          }"
          id="name"
          type="text"
          name="name"
          placeholder="Введите наименование товара"
          required
          @blur="inputHandler('title')"
        />
        <small
          class="helper-text"
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
            invalid: v$.link.$dirty && v$.link.$errors.length > 0,
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
          class="helper-text"
        >
          Поле является обязательным
        </small>
        <small
          class="helper-text__link"
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
            invalid: v$.price.$dirty && v$.price.$errors.length > 0,
          }"
          type="number"
          name="price"
          placeholder="Введите цену"
          required
          @blur="inputHandler('price')"
          id="price"
        />
        <small
          class="helper-text"
          v-if="v$.price.$dirty && v$.price.$errors.length > 0"
        >
          Поле является обязательным</small
        >
      </div>
      <button class="form-button" :disabled="!formValidated" type="submit">
        Добавить товар
      </button>
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
      // isValidate: false,
    };
  },
  validations() {
    return {
      title: { required }, // Matches this.firstName
      link: { required, url }, // Matches this.lastName
      price: { required },
    };
  },
  computed: {
    formData() {
      return {
        title: this.title,
        description: this.description,
        link: this.link,
        price: this.price,
      };
    },
    formValidated() {
      return !!(
        !this.v$.link.required.$invalid &&
        !this.v$.link.url.$invalid &&
        this.v$.link.$model &&
        !this.v$.title.required.$invalid &&
        this.v$.title.$model &&
        !this.v$.price.required.$invalid &&
        this.v$.price.$model
      );
    },
  },
  methods: {
    async submitHandler() {
      const result = await this.v$.$validate();
      if (result) {
        this.$emit("createNewObject", this.formData);
        setTimeout(() => {
          this.v$.$reset();
        }, 0);
      }
    },
    inputHandler(input) {
      if (!this.v$[input].$model) {
        this.v$[input].$touch();
      }
    },
    clearForm() {
      this.title = "";
      this.description = "";
      this.link = "";
      this.price = "";
    },
  },
};
</script>

<style lang="scss">
.menu-heading {
  margin-bottom: 16px;
  font-size: 28px;
  line-height: 35.2px;
  color: rgba(63, 63, 63, 1);
}
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
.invalid {
  border: 1px solid #ff8484;
}
.main-from-item {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.form-button {
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 10px;
  background-color: #7bae73;
  color: #fff;

  &:disabled {
    background-color: #eeeeee;
    color: #b4b4b4;
  }
  &:hover {
    box-shadow: 0px 1px 3px rgba(80, 130, 0, 0.3),
      0px 1px 3px rgba(0, 141, 77, 0.3);
  }
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
  padding-left: 16px;
  border: none;
  background-color: #fffefb;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  outline: none;
}
input:hover {
  box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.04), 0px 4px 8px rgba(0, 0, 0, 0.02);
}
input:focus {
  box-shadow: 0px 2px 7px rgba(0, 0, 0, 0.04), 0px 8px 12px rgba(0, 0, 0, 0.07);
}
input:active {
  box-shadow: none;
}
input::-webkit-input-placeholder {
  color: #b4b4b4;
  font-size: 12px;
  line-height: 15.08px;
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
  outline: none;
}
textarea::-webkit-input-placeholder {
  color: #b4b4b4;
  font-size: 12px;
  line-height: 15.08px;
}

textarea:hover {
  box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.04), 0px 4px 8px rgba(0, 0, 0, 0.02);
}
textarea:focus {
  box-shadow: 0px 2px 7px rgba(0, 0, 0, 0.04), 0px 8px 12px rgba(0, 0, 0, 0.07);
}
textarea:active {
  box-shadow: none;
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
