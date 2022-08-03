<template>
  <div>
    <div :class="['card created',{'delete':list.isDelete}]" >
      <div class="card-body" @dblclick="list.isEdit = true">
        <div class="d-flex justify-content-between">
          <input type="text" v-if="list.isEdit" @keyup.enter="list.isEdit = false" class="form-control w-50 zoomIn" v-model="list.message">
          <div v-else class="w-50">
            <input type="checkbox" v-model="list.isDone" class="form-check-input me-3" :id="'inputCheck'+list.id">
            <label :for="'inputCheck'+list.id" :class="['form-label',{'done':list.isDone}]">{{ list.message }}</label>
          </div>
          <div>
            <i class="fa-solid fa-pen-to-square text-primary me-3" @click="list.isEdit = true" style="cursor: pointer"></i>
            <i class="fa-solid fa-trash-can text-danger" @click="list.isDelete=true,del(list.id)" style="cursor:pointer;"></i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListItems",
  props : {

  },
  data() {
    return {
      list : {
        type : Object,
        required : true
      }
    }
  },
}
</script>

<style scoped>

</style>