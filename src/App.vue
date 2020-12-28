<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center pt-5 pb-5">Calories Counter</h1>
      </div>  
    </div>
    <div class="row">
      <div class="col-lg-4 col-sm-12">
        <fruitsList :data='fruits'></fruitsList> 
      </div> 
      <div class="col-lg-4 col-sm-12">
        <p>test 2</p>
      </div> 
      <div class="col-lg-4 col-sm-12">
        <p>test 3</p>
      </div> 
    </div> 
  </div>  
</template>

<script>
  import {data} from './assets/data.js';
  import fruitsList from './components/FruitsList.vue';

 export default {
   components: {
     fruitsList: fruitsList
   },
   data: function(){
    return {
       fruits: data
    }
  }
 }
</script>

