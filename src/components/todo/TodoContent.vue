<template>
    <div class="todo-list">
        <ul class="todo-ul">
            <li v-for="(todo,index) in todos" class="todo-li">
                <input type="checkbox" class="check-todo" :checked="todo.completed" @click="selecTodo(index,todo)"/> 
                <input type="text" :class="todo.completed?'todo-li-input completed':'todo-li-input'" :name="todo.value" :value="todo.value" />
                <button class="todo-li-delete" @click="deleteTodo(index)">x</button>
            </li>
        </ul> 
    </div>
</template>
<script>
export default {
    data(){
        return{
            idx:-1
        }
    },
    props:{
        todos:Array,
        required:true
    },
    methods:{
        selecTodo:function(e,d){
            this.idx=e;
            d.completed=!d.completed;
            this.$emit('selecTodo',e,d);
        },
        deleteTodo:function(index){
            this.$emit('deleteTodo',index);
        }
    }
}
</script>
<style>
.todo-ul{
    list-style: none;
    margin:0;
    padding:0;
}
.todo-li{
    float: left;
    width: 100%;
    border: 1px solid #ababab;
}
.check-todo{
    user-select: none;
    width: 18px;
    height: 18px;
    border: 3px solid #333333;
    display: inline-block;
    cursor: pointer;
    -webkit-border-radius: 5px;
    border-radius: 5px;
    float: left;
    margin: 12px 10px 0 10px;
}
.todo-li-input{
    float: left;
    width: 90%;
    height: 40px;
    font-size: 26px;
    border: 0px;
    outline:none;
    cursor: pointer;
}
.completed{
   color:#ababab;
   font-style: oblique;
   text-decoration:line-through; 
}
.todo-li-delete{
    float: right;
    margin: 12px 10px 0 0;
}

</style>


