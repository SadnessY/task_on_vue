<template>
  <div class="PCard">
    <h1>Добавление товара</h1>
    <div class="PCard" style="margin-top: 30px">
      <p>Наименование товара <img src="@/Rectangle32.png" alt=""></p>
      <input type="text" v-model="product.title" placeholder=" Введите наименование товара">
      <p>Описание товара</p>
      <input type="text" v-model="product.body" placeholder=" Введите описание товара">
      <p>Ссылка на изображение товара <img src="@/Rectangle32.png" alt=""></p>
      <input type="text" v-model="product.imageUrl" placeholder=" Введите ссылку">
      <p>Цена товара <img src="@/Rectangle32.png" alt=""></p>
      <input type="text" v-model="product.price" placeholder=" Введите цену">
      <button @click="addProductCard" class="btn">Добавить товар</button></div>
  </div>
</template>

<script>
import { required } from 'vuelidate/lib/validators'
export default {
  name: "AddProd",
  components: {
  },
  data() {
    return {
      product: {
        title: '',
        body: '',
        imageUrl: '',
        price: '',
      },
    }
  },
  validation: {
    product: {
      title: {required},
      price: {required},
      imageUrl: {required},
    },
  },
  computed: {
    nameErrors() {
      const errors = [];
      if (!this.$v.product.name.required) errors.push('Поле является обязательным')
    },
  },
  methods: {
    addProductCard() {
      console.log(this.product)
      this.product.id = Date.now();
      this.$emit('create', this.product)
      this.product = {
        title: '',
        body: '',
        imageUrl: '',
        price: '',
      }
    }
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