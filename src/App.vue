<script setup>
import { ref, computed } from "vue";
let newItem = ref("");
let items = ref([
  {text:"piim", done: true}, 
  {text:"viin", done: false}, 
  {text:"leib", done: true}, 
  {text:"õlu", done: false}, 
  {text:"banaan", done: true},
]);

function add() {
  if (newItem.value.trim() !== "") {
    items.value.push({test: newItem.value, done: false});
  }
  newItem.value = '';
}

let doneItems = computed(() => items.value.filter(item => item.done));
let toDoItems = computed(() => items.value.filter(item => !item.done));

</script>

<template>
  <div class="container mt-2">
    <div class="field has-addons">
      <div class="control is-expanded">
        <input class="input" type="text" v-model="newItem" @keydown.enter="add">
      </div>
      <div class="control">
        <button class="button is-info" @click="add">Add</button>
      </div>
    </div>
    <div class="content">
      <h1>All Items</h1>
      <ul>
        <li v-for="item in items">
          {{ item.text }}
          <input type="checkbox" v-model="item.done">
        </li>
      </ul>

      <h1>Done Items</h1>
      <ul>
        <li v-for="item in doneItems">
          {{ item.text }}
          <input type="checkbox" v-model="item.done">
        </li>
      </ul>

      <h1>ToDo Items</h1>
      <ul>
        <li v-for="item in toDoItems">
          {{ item.text }}
          <input type="checkbox" v-model="item.done">
        </li>
      </ul>
    </div>
  </div>
</template>
