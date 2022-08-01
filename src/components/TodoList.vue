<template>
    <div>
    <Todo v-for ="todo in todos"
         :key="todo.id"
         :todo="todo"
         @toggle-checkbox="toggleCheckBox"
         @click-delete="deleteTodo"/>
    </div>
</template>
<script>
import Todo from '@/components/Todo.vue';
export default {
    components:{
        Todo
    },
    props:{
        todos: {
            type : Array,
            required : true
        }
    },
    methods :{    //id랑 checked값을 부모 컴포넌트로 보내준다
        toggleCheckbox(value){
            this.$emit('toggle-checkbox',value)
            }
       ,
        deleteTodo(){
            this.$emit('click-delete', this.todo.id);
        }
    },

};
</script>

<style lang="scss" scoped>

</style>