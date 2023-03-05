<script setup>
import { ref, computed } from "vue";

const name = "Vue dinámico";
const arrayFavoritos = ref([])


const counter = ref(0);
const increment = () => {
  counter.value++;
};

const decrement = () => {
  counter.value--;
};

const reset = () => {
  counter.value = 0;
}

const add = () => {
arrayFavoritos.value.push(counter.value)
};

const bloquearBtnAdd = computed(() =>{
const numSearch = arrayFavoritos.value.find((num) => num === counter.value);
console.log(numSearch);
if(numSearch === 0) return true;
return numSearch ? true : false;
});

const classCounter = computed (() => {
if(counter.value === 0){
  return 'zero'
}
if(counter.value > 0){
  return 'positive'
}

if(counter.value < 0){
  return 'negative'
}
});
</script>

<template>

  <div class="container text-center, mt-3">
  <h1>Hola {{ name.toUpperCase() }}</h1>

<h2 :class="classCounter">{{ counter }}</h2>

<div class="btn-group">
  <button @click="increment" class="btn btn-success">Aumentar</button>
<button @click="decrement" class="btn btn-danger">Decrementar</button>
<button @click="reset" class="btn btn-secondary">Resetear</button>
<button @click="add" :disabled="bloquearBtnAdd">Add</button>
</div>

{{ arrayFavoritos }}
<ul class="list-group mt-4">

<li class="list-group-item" v-for="(num, index) in arrayFavoritos" :key="index">
  {{ num }}
</li>

</ul>
</div>
</template>


<style>
h1{

  color: rgb(255, 0, 0);

}
.positive {
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: peru;
}
</style> 