<template>
  <div class="p-5">

    <h4 class="text-primary">{{ title }}</h4>

    <p class="w-75 my-color">Lorem ipsum dolor sit amet, consectetur adipisicing elit. A assumenda cupiditate debitis distinctio dolorum earum eligendi ex iusto libero, molestiae necessitatibus, obcaecati placeat possimus quidem repellat sequi voluptatem voluptates, voluptatum?</p>

    <HelloWorld></HelloWorld>

    <i class="fa fa-house fa-4x"></i>

    <h3 class="my-3">Total List{{ lists.length > 1 ? "s" : "" }} <span class="badge rounded bg-primary">{{ total }}</span></h3>

    <input type="text" class="form-control w-50" v-model="newList" @keyup.enter="AddList()">

    <ul class="list-unstyled">
      <li class="list-group-item" v-for="list in  lists" :key="list">
        <div class="card w-50">
          <div class="card-body">
            <p class="m-0">{{ list }}</p>
          </div>
        </div>
      </li>
    </ul>

    <img class="w-50 rounded shadow" src="./assets/manchester-united-stadium-wallpaper-preview.jpg" alt="manu">

  </div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld";
export default {
  components : {
    HelloWorld
  },
    data(){
      return {
        name : "App",
         title : "Vue Cli Test",
         newList : "",
         lists : [],
      }
    },
  computed: {
    total() {
      return this.lists.length;
    }
  },
  methods: {
    AddList() {
        this.lists.push(this.newList);
        this.newList = "";
    }
  },
}
</script>

<style scoped>

</style>
