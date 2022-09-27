<template>
  <div class="Catalog">
    <ProdItem @edit="$emit('edit', product)" @remove="$emit('remove', product)" :key="product.id" :product="product" v-for="product in products"/>
  </div>
</template>

<script>
import ProdItem from "@/components/ProdItem";
export default {
  name: "CatalogProd",
  components: {
    ProdItem
  },
  props: {
    products: {
      type: Array,
      required: true,
    }
  }
}
</script>

<style scoped>
.Catalog {
  position: relative;
  top: 40px;
  display: flex;
  flex-flow: row;
  max-width: 1200px;
  flex-flow: wrap;
}

</style>