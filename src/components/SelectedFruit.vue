<template>
  <ul class="list-group">
    <li 
      v-for="item in selected"
      :key='item.name'
      class="list-group-item d-flex justify-content-between align-items-center">
      <p class="mb-0">{{ item.name}} ({{ item.calories}} kcal)</p>
      <input 
      @input="handleQuantity($event, item.name)"
      class="w-25 ml-auto mr-2" 
      type='number' 
      min='0' 
      max='50'/>
      <span 
        @click='handleRemove($event, item.name)'
        class="badge rounded-pill bg-danger text-white">X</span>
    </li>  

  </ul>  
</template>

<script>
export default {
  props: {
    selected: Array,
    handleQuantity: Function,
    handleRemove: Function
  }
}
</script>

<style scoped>
  .badge:hover{
    cursor: pointer;
  }
</style>