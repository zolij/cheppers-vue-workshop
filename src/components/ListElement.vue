<template>
  <div>
    {{index + 1}}. 
    <input type="text" :value="product" @keyup="editProduct($event)">
    <input type="number" :value="price" @keyup="editPrice($event)">
    <button @click="deleteEntry">Delete</button>
  </div>
</template>

<script>
export default {
  props: ["price", "product", "index"],
  methods: {
    deleteEntry() {
      this.$emit("delete-entry", this.index);
    },
    editProduct(e) {
      this.edit({
        price: this.price,
        product: e.target.value
      });
    },
    editPrice(e) {
      this.edit({
        price: e.target.value,
        product: this.product
      });
    },
    edit(values) {
      this.$emit("edit", {
        index: this.index,
        values: values
      });
    }
  }
};
</script>

<style>

</style>
