<template>
  <div class="PCard">
    <h1>Добавление товара</h1>
    <form class="PCard" style="margin-top: 30px" @submit.prevent>
      <p>Наименование товара <img src="@/Rectangle32.png" alt=""></p>
      <input :class="$v.product.title.$error ? 'is-invalid' : ''" type="text" v-model="product.title"  placeholder=" Введите наименование товара">
      <p style="color: red" v-if="$v.product.title.$dirty && !$v.product.title.required">Поле является обязательным</p>
      <p>Описание товара</p>
      <input type="text" v-model="product.body" placeholder=" Введите описание товара">
      <p>Ссылка на изображение товара <img src="@/Rectangle32.png" alt=""></p>
      <input :class="$v.product.imageUrl.$error ? 'is-invalid' : ''" type="text" v-model="product.imageUrl" placeholder=" Введите ссылку">
      <p style="color: red" v-if="$v.product.imageUrl.$dirty && !$v.product.imageUrl.required">Поле является обязательным</p>
      <p style="color: red" v-else-if="$v.product.imageUrl.$dirty && !$v.product.imageUrl.url">Неверно указан адрес изображения</p>
      <p>Цена товара <img src="@/Rectangle32.png" alt=""></p>
      <input :class="$v.product.price.$error ? 'is-invalid' : ''" type="text" v-model="product.price" placeholder=" Введите цену">
      <p style="color: red" v-if="$v.product.price.$dirty && !$v.product.price.required">Поле является обязательным</p>
      <button v-if="!redacting" @click="checkForm" class="btn">Добавить товар</button>
      <button v-if="redacting" @click="checkForm" class="btn">Изменить товар</button>
      <button @click="fill_lines" class="btn">Обновить поля</button>
    </form>
  </div>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, url } from 'vuelidate/lib/validators'
export default {
  mixins: [validationMixin],
  name: "AddProd",
  components: {  },
  data() {
    return {
      product: {
        id: '',
        title: '',
        body: '',
        imageUrl: '',
        price: '',
      },
      redacting: false,
    }
  },
  props: {
    editProd: {
      type: Object,
    }
  },
  validations: {
    product: {
      title: { required },
      price: { required },
      imageUrl: { required, url },
      },
    },
  methods: {
    checkForm() {
      this.$v.product.$touch()
      if (!this.$v.product.$error) {
        if (this.redacting) {
          return this.editProductCard()
        }else {
          return this.addProductCard()
        }
      }
    },
    fill_lines() {
      this.product.id = this.editProd.id
      this.product.title = this.editProd.title
      this.product.body = this.editProd.body
      this.product.imageUrl = this.editProd.imageUrl
      this.product.price = this.editProd.price
      this.redacting = true
    },
    editProductCard() {
      console.log(this.product)
      this.$emit('addEdit', this.product)
      this.redacting = false
      this.product = {
        title: '',
        body: '',
        imageUrl: '',
        price: '',
      }
    },
    addProductCard() {
      this.product.id = Date.now();
      this.$emit('create', this.product)
      this.product = {
        title: '',
        body: '',
        imageUrl: '',
        price: '',
      }
    },
  }
}


</script>

<style scoped>
input {
  width: 284px;
  height: 36px;
  background: #FFFEFB;
  border: none;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  padding-left: 20px;
}
.is-r {
  background: #7BAE73;
}
.is-invalid {
  border: 1px solid red;
  border-radius: 10px;
}
.btn {
  width: 284px;
  height: 36px;
  background: #EEEEEE;
  border-radius: 10px;
  margin-top: 35px;
  font-family: 'Inter';
  font-style: normal;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  text-align: center;
  letter-spacing: -0.02em;
  color: #B4B4B4;
  border: none;
}
.PCard {
  position: relative;
  left: 50px;
  display: flex;
  flex-flow: column wrap;
  margin-right: 20px;
}
h1 {
  font-size: 25px;
}
</style>