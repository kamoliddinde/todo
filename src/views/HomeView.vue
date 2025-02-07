<script setup>

</script>

<template>
  <main>
    <h1>Todo List</h1>
    <form @submit.prevent="addTodo" >
      <input required type="text" placeholder="Add a new todo" v-model="title" />
      <button>Add</button>
    </form >
    <div class="todos-container"> 
      <div v-for="todo in todos" :key="todo.id" class="todo-item">
        <div class="todo-item-left">
          <input type="checkbox" :checked="todo.completed" @change="toggleTodo(todo.id)"/>
          <p class="todo-title" :class="{completed: todo.completed}" >{{ todo.title }}</p>
        </div>
       <div class="todo-item-left">
          <button class="btn-delete">Delete</button>
          <button class="btn-edit">Edit</button>
       </div>
      </div>
    </div>
  </main>
</template>
 <script setup>
 import { ref  } from "vue";
 const title = ref("");
 const addTodo = () => {
  const todoObj = {
    title: title.value,
    id: new Date().getTime(),
    completed: false,
    
  };
todos.value.push(todoObj);
title.velue="";
  
 };
 const todos = ref([
  {
    id: 1,
    title: "todo 1",
    completed: true,
  }
 ]);

 const toggleTodo = (id) => {
 const todo = todos.value.find((todo) => todo.id === id);
  todo.completed = !todo.completed;
 
 };
</script>
<style>
  main{
    background-color: #fff;
    width: 500px;
    margin: 100px auto;
    padding: 20px ;
  }
  h1{
    text-align: center;
  }
  form{
    display: flex;
    gap: 10px;
  }
  input{
    flex: 1;
    padding: 10px;
    border: 1px solid blue;
  }
  button{
    padding: 10px;
    background-color: blue;
    color: white;
    border: none;
    cursor: pointer;
  }
  .todos-container{
    margin-top: 20px;
  }
  .todo-item{
    display: flex;
    justify-content: space-between;
    padding: 5px;
    border: 1px solid #ccc;
    margin-top: 10px;
    background-color: #eee;
    margin-bottom: 10px;
  }
  .todo-item-left{
    display: flex;
    gap: 10px;
    align-items: center;
  }
  .todo-item-left p{
    display: flex;
    gap: 10px;
  }
  .btn-delete{
    background-color: red;
    color: white;
    border: none;
    cursor: pointer;
  }
  .btn-edit{
    background-color: blue;
    color: white;
    border: none;
    cursor: pointer;
  }
  .todo-title.completed{
    text-decoration: line-through;
  }
</style>