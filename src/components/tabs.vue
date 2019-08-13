<template>
    <div>
        <span>{{unfinishedTodoLength}} items</span>
        <br />
        <span class="tabs">
            <span style="margin-right:10px;" v-for="state in states" :key="state" @click="toggleFilter(state)">{{state}}</span>
        </span><br />
        <span @click="clearAllCompleted">clear Completed</span>
    </div>
</template>
<script>
export default {
    props:{
        todos:{
            type:Array,
            required:true
        }
    },
    data(){
        return{
            states:['all','active','completed']
        }
    },
    computed:{
       unfinishedTodoLength(){
           return this.todos.filter(todo => !todo.completed).length
       }
    },
    methods:{
        toggleFilter(state){
            this.$emit('toggle',state)
        },
        clearAllCompleted(){
            this.$emit('clearAll')
        }
    }

}
</script>
<style scoped>

</style>