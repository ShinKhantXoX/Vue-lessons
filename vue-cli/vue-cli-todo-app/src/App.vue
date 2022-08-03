<template>
  <div class="container py-5" >
    <div class="row">
      <div class="col-6">
        <div class="card">
          <div class="card-body">
            <ListTitle title="Vue Todo App"></ListTitle>
            <div class="d-flex justify-content-around">
              <input type="text" v-model="newMessage" placeholder="Say Something" @keyup.enter="add()" class="form-control form-control-lg me-2">
              <button class="btn btn-primary" @click="add()">
                <i class="fa fa-plus"></i>
              </button>
            </div>
            <div class="d-flex justify-content-between my-3">
              <h6 class="text-black-50">Job List{{ lists.length > 1 ? "s" : "" }}</h6>
              <p v-if="lists.length > 0 && doneTotal===lists.length" class="p-1 bg-success text-light badge rounded fadeInRight">Well Done <i class="fa-solid fa-check"></i></p>
              <p v-else class="p-1 bg-primary text-light badge rounded">Done {{ doneTotal }}</p>
            </div>
            <ListItems v-for="list in lists" :key="list.id" list="list"></ListItems>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ListTitle from "@/components/ListTitle";
import ListItems from "@/components/List";



export default {
  components: {ListItems, ListTitle},
  data(){
    return {
      currentId : 0,
      title : "Vue Todo List",
      newMessage : "",
      lists : [

      ]
    }
  },
  computed : {
    doneTotal() {
      return this.lists.filter(el => el.isDone === true).length
    }
  },
  methods : {
    add() {
      this.currentId++;
      this.lists.push(
          {
            id : this.currentId,
            message : this.newMessage,
            isDone : false,
            isEdit : false,
            isDelete : false
          }
      );
      this.newMessage = "";
    },
    del(x){
      // if(confirm("Are you sure to delete?")) {
      setTimeout(() => this.lists = this.lists.filter(el => el.id !== x),500)
      // }
    }
  }
}
</script>

<style >
.done{
  text-decoration: line-through;
  animation: 0.5s bounceIn;
}
.created{
  animation: 0.5s fadeInDown;
}
.fadeInRight{
  animation: 0.5s fadeInRight;
}
.zoomIn{
  animation: 0.5s zoomIn;
}
.delete{
  animation: 0.5s fadeOutUp;
}
</style>