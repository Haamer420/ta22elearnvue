<script setup>
import { reactive, ref } from 'vue';
import ItemList from './components/ItemList.vue';
const message = ref('Hello vue');
let i = 1;
const items = reactive([
  {id:i++,name:'leib', isDone: false },
  {id:i++,name:'sai', isDone: true },
  {id:i++,name:'piim', isDone: false },
  {id:i++,name:'kommid', isDone: true },
]);

const doneItems = computed(() => {
  return items.filter(item => item.isDone)
});

const toDoItems = computed(() => {
  return items.filter(item => !item.isDone)
});

function add(){
  items.push({id:i++, name:message.value, isDone: false});
}
</script>

<template>
  <button @click="add">Click me</button>
  <input type="text" v-model="message">
  <ItemList :items="items" title="All Items"></ItemList>
  <ItemList :items="doneItems" title="Done Items"></ItemList>
  <ItemList :items="toDoItems" title="ToDo Items"></ItemList>
</template>
