<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center pt-5 pb-5">Calories Counter</h1>
      </div>  
    </div>
    <div class="row">
      <div class="col-lg-4 col-sm-12">
        <fruitsList 
        :addFruitFn='addFruit'
        :data='fruits'></fruitsList> 
      </div> 
      <div class="col-lg-4 col-sm-12">
        <selectedFruitsList
        :handleRemove="handleRemove" 
        :handleQuantity="handleQuantity"
        :selected="selected"></selectedFruitsList>
      </div> 
      <div class="col-lg-4 col-sm-12">
        <p>Total: {{ total }} kcal</p>
      </div> 
    </div> 
  </div>  
</template>

<script>
  import {data} from './assets/data.js';
  import fruitsList from './components/FruitsList.vue';
  import selectedFruitsList from './components/SelectedFruit.vue';

 export default {
   components: {
     fruitsList: fruitsList,
     selectedFruitsList: selectedFruitsList
   },
   data: function(){
    return {
       fruits: data,
       selected: [],
    }
  },
  computed: {
    total(){
      return this.selected.reduce((acc, curr) => acc + (curr.calories * curr.count), 0);
    }
  },
  methods: {
    addFruit: function(data){
      data.count = 0;
      if(this.selected.length === 0){
        this.selected.push(data);
      }else{
        let k = this.selected
                  .map(el => el.name)
                  .filter((el,i, arr) => arr.indexOf(el) === i)
        if(k.indexOf(data.name) === -1){
          this.selected.push(data);
        }else{
          return;
        }
      }
    },
    handleQuantity: function(n, item){
      let q = Number(n.target.value);
      let f =  item;
      let temp = this.selected.map(el => el.name === f ? {...el, count: q} : el);
      this.selected = temp;
    },
    handleRemove: function($event, item){
      let temp = this.selected.filter(el => el.name !== item);
      this.selected = temp;
    }
  }
 }
</script>

