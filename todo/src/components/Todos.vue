<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todosInChildren">
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
    name: "Todos",
    props: ["todos"],
    watch: {
        todos(newValue){
            this.todosInChildren = newValue;
        }
    },
    components:{
        TodoItem
    },
    data(){
        return{
            todosInChildren: this.todos
        }
    }
}
</script>

<style scoped>

</style>