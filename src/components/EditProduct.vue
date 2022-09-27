<template>
  <div class="PCard">
    <h1>Добавление товара</h1>
    <div class="PCard" style="margin-top: 30px"><p>Наименование товара<img src="@/Rectangle32.png" alt=""></p>
      <MyInput class="input" v-model="product.title" placeholder="Введите наименование товара" />
      <p>Описание товара</p>
      <input class="input" v-model="product.body" style="height: 108px" placeholder="Введите описание товара">
      <p>Ссылка на изображение товара<img src="@/Rectangle32.png" alt=""></p>
      <input class="input" v-model="product.imageUrl" placeholder="Введите ссылку">
      <p>Цена товара<img src="@/Rectangle32.png" alt=""></p>
      <input class="input" v-model="product.price" placeholder="Введите цену">
      <button @click="addProductCard" class="btn">Добавить товар</button></div>
  </div>
</template>

<script>
export default {
  name: "EditProduct",
}
</script>

<style scoped>

</style>