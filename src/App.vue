<template>
  <div id="app">
    <div v-if="!printMode">
    <entry @new-entry="addToList" />
    <list :list="list" @delete-at-index="deleteAtIndex" @edit="editElement" />
    </div>
    <div v-if="printMode">
      <div v-for="(entry, index) in list">
        {{entry.product}} - {{entry.price}}
      </div>
    </div>
    <button v-if="list.length > 0  && !printMode" @click="viewPrint">Print</button>
    <button v-if="printMode" @click="reset">New list</button>
  </div>
</template>

<script>
import Entry from "./components/Entry.vue";
import List from "./components/List.vue";

export default {
  data() {
    return {
      list: [],
      printMode: false
    };
  },
  methods: {
    addToList(payload) {
      if (this.validate(payload)) {
        this.list.push(payload);
      }
    },
    deleteAtIndex(payload) {
      this.list.splice(payload, 1);
    },
    editElement(payload) {
      this.$set(this.list, payload.index, payload.values);
    },
    viewPrint() {
      this.printMode = true;
    },
    reset() {
      this.list = [];
      this.printMode = false;
    },
    validate(payload) {
      if (payload.product === "" || payload.price === 0) {
        alert("You should check your input!");
        return false;
      } else {
        return true;
      }
    }
  },
  components: { Entry, List }
};
</script>

<style>

</style>
