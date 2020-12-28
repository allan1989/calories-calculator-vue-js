<template>
  <ul class="list-group">
    <li 
      class="list-group-item"
      v-for="fruit in data" 
      @click="addFruit(fruit.name)"
      :key='fruit.name'>{{ fruit.name }}</li>
  </ul>  
</template>

<script>
export default {
  props: ['data'],
  methods: {
    addFruit: function(e){
      console.log(e)
    }
  }

}
</script>

<style scoped>
  .list-group-item:hover{
    cursor: pointer;
  }
</style>
