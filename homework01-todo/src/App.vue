<template>
<div id="app">
  <div class="wrap">
    <div class="todo-lists">
      <h3>Todo List</h3>
      <ul>
        <listitem :paramList='todoLists'></listitem>     
        <!-- <list-item v-for="i in todoLists" :key="i.id"></list-item> -->
      </ul>
    </div>

    <div class="done-lists">
      <h3>Done List</h3>
      <ul>
        <listitem :paramList='doneLists'></listitem>
        <!-- <list-item v-for="i in doneLists" :key="i.id"></list-item> -->
      </ul>
    </div>
  </div>
</div>


</template>

<script>
import listitem from './components/ListItem.vue';

export default {
  name: 'App',
  components:{
    listitem
  },
  data() {
    return {
      lists: [{
          id: 'task001',
          title: '選項 1',
          isDone: false
        },
        {
          id: 'task002',
          title: '選項 2',
          isDone: false
        },
        {
          id: 'task003',
          title: '選項 3',
          isDone: false
        },
      ]
    }
  },
  computed: {
    todoLists() {
      return this.lists.filter(d => !d.isDone)
    },
    doneLists() {
      return this.lists.filter(d => d.isDone)
    },
  }
}
</script>

<style>
h3 {
  margin-bottom: 1rem;
}

.wrap {
  position: relative;
  display: block;
  overflow: hidden;
}

.todo-lists, .done-lists {
  display: block;
  max-width: 150px;
  width: 45%;
  height: 200px;
  margin-right: 4%;
  float: left;
  border: 1px solid #ccc;  
  padding: 1rem;
}


</style>
