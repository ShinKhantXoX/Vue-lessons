<template>
  <div class="p-5">
    <h4 class="d-flex justify-content-start align-items-center">
      <ListTitle title="Fruits List"></ListTitle>
      <span class="badge badge-pill bg-primary ms-3">{{ fruits.length }}</span>
    </h4>
    <ul class="list-group">
      <List class="list-group-item" v-for="(fruit,index) in fruits" :key="index" :list-data="fruit" :current-index="index" @toParent="run"></List>
    </ul>


  </div>
</template>

<script>

import List from "@/components/List";
import ListTitle from "@/components/ListTitle";

export default {
  name : "App",
  components : {List,ListTitle},
  data() {
    return {
      fruits: ["apple", "orange", "mango"]
    }
  },
  methods: {
    run(x) {
      this.fruits.splice(x,1);
        console.log(x)
    }
  },
}
</script>

<style scoped>

</style>