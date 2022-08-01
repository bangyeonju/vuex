<template>
<div id="app" class="container">
  <h1 class="text-center">Todo App</h1>
  <AddTodo @add-todo="addTodo"/>
  <hr>
  <TodoList 
         :todos="todos"
         @toggle-checkbox="toggleCheckBox"
         @click-delete="deleteTodo"
         />
         {{todos}}
</div>
</template>

<script>
import TodoList from '@/components/TodoList.vue';
import AddTodo from '@/components/AddTodo.vue';

export default {
  components: {
    TodoList,
    AddTodo
    },
   data(){
        return{
            todoText:'',
            todos:[
                {id:1, text:'buy a car',checked:false},
                {id:2, text:'play game',checked:false},
                ]
        }
    },
    methods :{
      addTodo(e){
        this.todos.push({
          id : Math.random(),
          text : e.target.value,
          checked : false
        });
        this.todoText='';
      },

      toggleCheckBox({id, checked}){
        const index = this.todos.findIndex(todo=>{
          return todo.id ===id;
        });
        this.todos[index].checked= checked;
      },
      deleteTodo(id){
        // const index = this.todos.findIndex(todo=>{
        //   return todo.id===id;
        // });
        // console.log(id);
        // this.todos.splice(index, 1);
        this.todos = this.todos.filter(todo=>todo.id!==id);
      }
    }
}
</script>

<style>

</style>
