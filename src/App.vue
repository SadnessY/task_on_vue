<template>
  <div id="app">
    <input placeholder="Поиск..." class="search_input" v-model="searchQuery" type="text">
    <div style="display:flex;">
      <AddProd @create="addProductCard" @addEdit="editProductCard" :editProd="editProd"/>
      <MySelect />
      <CatalogProd @remove="removeProduct" @edit="get_ed_pr" :products="searching_for_name" />
    </div>
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
        {id: 7, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 8, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 9, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 10, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 11, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
        {id: 12, title: "Наименование товара", body: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк", imageUrl: "https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80", price: "10000 руб."},
      ],
      title: '',
      body: '',
      imageUrl: '',
      price: '',
      searchQuery: '',
      editProd: null,
    }
  },
  methods: {
    addProductCard(product) {
      this.products.push(product)
      this.saveProds()
    },
    removeProduct(product) {
      this.products = this.products.filter(p => p.id !== product.id)
      this.saveProds()
    },
    get_ed_pr(product) {
      this.editProd = product
    },
    editProductCard(product) {
      this.products = this.products.filter(p => p.id !== product.id)
      this.products.push(product)
      this.saveProds()
    },
    saveProds() {
      const parsed = JSON.stringify(this.products);
      localStorage.setItem('products', parsed);
    }
  },
  mounted() {
    if (localStorage.getItem('products')) {
      try {
        this.products = JSON.parse(localStorage.getItem('products'));
      } catch(e) {
        localStorage.removeItem('products');
      }
    }
  },
  computed: {
    searching_for_name() {
      return this.products.filter(prod => prod.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.search_input {
  border: 2px solid black;
  width: 700px;
  left: 500px;
  top: 50px;
  position: absolute;
  padding-left: 20px;
  height: 36px;
  border-radius: 10px;
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
