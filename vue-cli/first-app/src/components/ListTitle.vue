<template>
  <div>
      <h4>{{ title }}</h4>
  </div>
</template>

<script>
export default {
  name : "ListTitle",
  props : {
    title : {
      default : "This is Fruits List"
    }
  }
}
</script>

<style scoped>

</style>