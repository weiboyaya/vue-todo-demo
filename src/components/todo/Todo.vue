<template>
    <div class="todo">
        <TodoHead @addTodo="addTodo"></TodoHead>
        <TodoContent :todos="todos" @deleteTodo="deleteTodo" @selecTodo="selecTodo"></TodoContent>
        <TodoFooter :size="size" :clickSpan="clickSpan" @clearCompleted="clearCompleted" @selecAll="selecAll" @selecActive="selecActive" @selecCompleted="selecCompleted"></TodoFooter>
    </div>
</template>
<script>
import TodoHead from '../todo/TodoHead.vue'
import TodoFooter from '../todo/TodoFooter.vue'
import TodoContent from '../todo/TodoContent.vue'

export default {
    data(){
        return {
            todos:[],
            tempTodos:[],
            clickSpan:"",
            size:0
        }
    },
    components:{
        TodoHead,
        TodoFooter,
        TodoContent
    },
    methods:{
        addTodo:function(e){
            this.clickSpan="all";
            if(this.tempTodos.length>0){
                this.todos=JSON.parse(JSON.stringify(this.tempTodos));
            }
            this.todos.unshift(e);
            this.size++;
            
        },
        deleteTodo:function(index){
            if(!this.todos[index].completed){
                this.size--;
            }
            this.todos.splice(index,1);
            
        },
        selecTodo:function(index,d){
            for(var i=0;i<this.todos.length;i++){
                if(i==index){
                    this.todos[i]=d;
                }
            }
            d.completed?this.size--:this.size++;
        },
        selecAll:function(){
            this.clickSpan="all";
            if(this.tempTodos.length>0){
                this.todos=JSON.parse(JSON.stringify(this.tempTodos));
            }
        },
        selecActive:function(){
             this.clickSpan="active";
            if(this.tempTodos.length>0){
               this.todos=JSON.parse(JSON.stringify(this.tempTodos)); 
            }else{
                this.tempTodos=JSON.parse(JSON.stringify(this.todos));
            }
            for(var i=0;i<this.todos.length;i++){
                if(this.todos[i].completed){
                    this.todos.splice(i,1);
                    i--;
                }
            }
        },
        selecCompleted:function(){
             this.clickSpan="completed";
            if(this.tempTodos.length>0){
               this.todos=JSON.parse(JSON.stringify(this.tempTodos)); 
            }else{
                this.tempTodos=JSON.parse(JSON.stringify(this.todos));
            }
            for(var i=0;i<this.todos.length;i++){
                if(!this.todos[i].completed){
                    this.todos.splice(i,1);
                    i--;
                }
            }
        },
        clearCompleted:function(){
            this.clickSpan="all";
            if(this.tempTodos.length>0){
               this.todos=JSON.parse(JSON.stringify(this.tempTodos)); 
            }
            this.tempTodos=[];
            for(var i=0;i<this.todos.length;i++){
                if(this.todos[i].completed){
                    this.todos.splice(i,1);
                    i--;
                }
            }
        }
    }
}
</script>
<style>
.todo{
    text-align:center;
    width:60%;
    position: absolute;
    margin: auto;
    left: 0;
    right: 0;
    box-shadow: 8px 8px 20px #aba;
    border: 1px solid #ababab;
    overflow-x: hidden;
    overflow-y: auto;
    max-height: 60%;
}
</style>


