<template>
    <div class="todo-head">
        <input type="text" class="todo-head-input" placeholder="  What needs to be done?" @keydown.enter="inputTodo($event)" />
    </div>
</template>
<script>
export default {
    methods:{
        inputTodo:function(e){
            this.$emit('addTodo',{completed:false,
                value:e.target.value});
                e.target.value="";
        }
    }
}
</script>
<style>
.todo-head-input{
    width: 100%;
    height: 50px;
    font-size: 26px;
    font-style: oblique;
}
</style>
