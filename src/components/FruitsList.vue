<template>
  <ul class="list-group">
    <li 
      class="list-group-item"
      v-for="fruit in data" 
      @click="addFruitFn({name: fruit.name, calories: fruit.calories})"
      :key='fruit.name'>{{ fruit.name }}</li>
  </ul>  
</template>

<script>
export default {
  props: {
    data: Array,
    addFruitFn: Function
  },
}
</script>

<style scoped>
  .list-group-item:hover{
    cursor: pointer;
  }
</style>
