<template>
    <div class="todo-footer">
        <div class="todo-item-left">{{size}}个未完成任务</div>
        <div class="todo-status">
            <span id="all" :class="clickSpan=='all'?'click-span':'' " @click="selecAll" >全部</span>
            <span id="active" :class="clickSpan=='active'?'click-span':''" @click="selecActive">执行中</span>
            <span id="completed" :class="clickSpan=='completed'?'click-span':''" @click="selecCompleted">已完成</span>
        </div>
        <div class="todo-clear">
            <span id="clear" @click="clearCompleted">清空已完成</span>
        </div>
    </div>
</template>
<script>
export default {
    props:{
        clickSpan:{
            type:String,
            required:true
        },
        size:{
            type:Number,
            required:true
        }
        },
    methods:{
        selecAll:function(){
            this.$emit('selecAll');
        },
        selecActive:function(){
            this.$emit('selecActive');
        },
        selecCompleted:function(){
            this.$emit('selecCompleted');
        },
        clearCompleted:function(){
            this.$emit('clearCompleted');
        }
    }

}
</script>
<style>
.todo-footer{
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    height: auto;
}
.todo-item-left{
    float: left;
    width:20%;
    height: 40px;
     margin: 15px 0 0 0;
}
.todo-status{
    float: left;
    text-align: center;
    width:60%;
    height: 40px;
     margin: 15px 0 0 0;
}
.todo-clear{
    float: right;
     width:20%;
     height: 40px;
      margin: 15px 0 0 0;
}
.todo-status :hover{
    color:blue;
    font-weight: bold;
    border:1px solid #000;
}
.todo-clear :hover{
    color:blue;
    font-weight: bold;
    border:1px solid #000;
}
.todo-clear-hover{
    color:blue;
    font-weight: bold;
    border:1px solid #000;
}
.click-span{
    color:blue;
    font-weight: bold;
    border:1px solid #000;
}
</style>

