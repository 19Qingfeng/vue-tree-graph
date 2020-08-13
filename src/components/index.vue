<template>
    <div>
        <div class="wapper">
            <div class="row">
                <div class="col">
                    <div class="title">title</div>
                    <div class="body">body</div>
                    
                </div>
            </div>
            <div class="row">

            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"TreeMap",
    props:{
        treeData:Object
    },
    data() {
        return {}
    }
}
</script>
<style>
    .wapper {
        display:flex;
        text-align: center;
    }
    .title{
        background-color: #eee;
        width:100px;
        line-height: 30px;
        height: 30px;
    }
    .body{
        background-color: #777;
        width: 100px;
        height: 60px;
        line-height: 60px;
        position: relative;
    }
    .body::after{
        content: "";position: absolute;left:0;right:0;top:-15px;border-top:2px solid #ccc;
    }
</style>