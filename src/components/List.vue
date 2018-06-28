<template>
  <div>
    <list-element 
    v-for="(element, index) in list" 
    :key="index" 
    :price="element.price" 
    :product="element.product"
    :index="index"
    @delete-entry="deleteFromList"
    @edit="modifyElement"
    ></list-element>
  </div>  
</template>

<script>
import ListElement from "./ListElement.vue";
export default {
  props: ["list"],
  components: {
    ListElement
  },
  methods: {
    deleteFromList(payload) {
      this.$emit("delete-at-index", payload);
    },
    modifyElement(payload) {
      this.$emit("edit", payload);
    }
  }
};
</script>

<style>

</style>
