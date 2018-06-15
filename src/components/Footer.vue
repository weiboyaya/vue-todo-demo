<template>
    <div class="footer">
       <span>开发者：{{auther}}</span> 
    </div>
</template>
<script>
export default {
    data(){
        return{
            auther:"weibo"
        }
    }
}
</script>
<style>
.footer{
    text-align: center;
    font-size: 20px;
    font-family: 'Courier New', Courier, monospace;
    position: absolute;
    bottom: 20px;
    margin: auto;
    left: 0;
    right: 0;
}

</style>

