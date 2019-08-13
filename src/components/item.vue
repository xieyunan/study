<template>
    <div>
        <input 
        type="checkbox"
        class="toggle"
        v-model="todo.completed"
        >
        <label>{{todo.content}}</label>
        <button class="destory" @click="deleteTodo">删除</button>
    </div>
</template>
<script>
export default {
    props:{
        todo:{
            type:Object,
            required:true
        }
    },
    methods:{
        deleteTodo(){
            this.$emit('del',this.todo.id)
        }
    }
}
</script>