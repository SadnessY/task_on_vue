<template>
  <div id="app">
    <AddProd @create="addProductCard"/>
    <MySelect />
    <CatalogProd @edit="editProduct" @remove="removeProduct" :products="products" />
  </div>
</template>

<script>
import AddProd from "@/components/AddProd";
import CatalogProd from "@/components/CatalogProd";
import MySelect from "@/components/UI/MySelect";
export default {
  name: 'App',
  components: {
    MySelect,
    CatalogProd,
    AddProd,
  },
  data() {
    return {
      products: [
        {id: 1, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 2, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 3, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 4, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 5, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 6, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
      ],
      title: '',
      body: '',
      imageUrl: '',
      price: '',
    }
  },
  methods: {
    addProductCard(product) {
      this.products.push(product)
    },
    removeProduct(product) {
      this.products = this.products.filter(p => p.id !== product.id)
    },
    editProduct(product) {

    }
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

input {
  width: 284px;
  height: 36px;
  background: #FFFEFB;
  border: none;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

p {
  font-family: 'Source Sans Pro';
  font-style: normal;
  font-weight: 400;
  font-size: 10px;
  margin-bottom: 5px;
  margin-top: 5px;
  position: relative;
  display: flex;
  justify-content: flex-start;
}
img {
  width: 4px;
  height: 4px;
}
::placeholder {
  position: relative;
  left: 20px;
}
h1 {
  position: relative;
  left: 20px;
  display: flex;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: flex-start;
}
</style>
