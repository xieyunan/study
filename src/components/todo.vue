<template>
    <section class="real-app">
        <input 
        type="text" 
        class="add-input"
        autofocus="autofocus"
        placeholder="目标"
        @keyup.enter="addToDo"
        >
        <item :todo="todo" v-for="todo in todos" :key="todo.id"
        @del="deleteTodo"
        />
        <tabs :todos="todos"
        :filter ="filter"
        @toggle="toggleFilter"
        @clearAll="clearAllCompleted"
        />
    </section>
</template>
<script>
import item from './item.vue'
import tabs from './tabs.vue'
let id = 0;
export default {
    data(){
        return{
            todos:[],
        }
    },
    components:{
        item,tabs
    },
    computed:{
        // filteredTodos(){
        //     if(this.filter === 'all'){
        //         return this.todos
        //     }
        //     const completed = this.filter === 'componted'
        //     this.todos.filter(todo => completed === todo.completed)
        // }
    },
    methods:{
        addToDo(e){
            this.todos.unshift({
                id:id++,
                content:e.target.value.trim(),
                completed:false
            })
            e.target.value = ''
        },
        deleteTodo(id){
         this.todos.splice(this.todos.findIndex(todo=>todo.id === id),1)   
        },
        toggleFilter(state){
            this.filter =state

        },
        clearAllCompleted(){
           this.todos = this.todos.filter(todo => !todo.completed)
        }
    }
}
</script>
<style scoped>

</style>