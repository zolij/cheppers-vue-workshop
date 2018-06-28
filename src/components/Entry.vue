<template>
  <div>
  Product: <input type="text" v-model="newproduct">
  Price: <input type="number" name="" id="" v-model="newprice">
  <button @click="addNewEntry">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newproduct: "",
      newprice: 0
    };
  },
  methods: {
    addNewEntry() {
      this.$emit("new-entry", {
        product: this.newproduct,
        price: this.newprice
      });
      this.newproduct = "";
      this.newprice = 0;
    }
  }
};
</script>

<style>

</style>
