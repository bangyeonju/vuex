 <template>
<input v-model="todoText"
         type="text" 
         class="w-100"
         placeholder="Type todo"
         @keyup.enter="addTodo">
 </template>
 
 <script>
 export default {
      data(){
        return{
            todoText:'',
        }
      },
    methods :{
        addTodo(e) {
            this.$emit('add-todo', e.target.value);
        }
    }
 };
 </script>
 
 <style lang="scss" scoped>
 
 </style>