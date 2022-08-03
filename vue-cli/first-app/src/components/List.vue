<template>
      <li>
          {{ listData }}
        <button class="btn btn-primary" @click="toRun">Del</button>
      </li>
</template>

<script>
export default {
  name : "ListView",
  props : ["listData","currentIndex"],
  methods: {
    toRun() {
      this.$emit("toParent",this.currentIndex)
    }
  },
}
</script>

<style scoped>

</style>