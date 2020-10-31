<template>
    <div class="clearAllContainer">
        <button class="clearAllBtn"  @click="clearTodo">전체 삭제</button>
    </div>
</template>

<script>
    export default {
        name: "TodoFooter",
        methods: {
            clearTodo() {
                this.$emit('removeAll');
            },
        },
    }
</script>

<style scoped>

    .clearAllBtn {
        background:skyblue;
        color:black;
        border:none;
        position:relative;
        height:60px;
        font-size:1.6em;
        padding:0 2em;
        cursor:pointer;
        transition:800ms ease all;
        outline:none;
        border-radius: 5px 5px 5px 5px;
        width:20%;
        font-size:20px;
    }
    .clearAllBtn:hover {
        background:#fff;
        color:#1AAB8A;
    }
    .clearAllBtn:before,.clearAllBtn:after{
        content:'';
        position:absolute;
        top:0;
        right:0;
        height:2px;
        width:0;
        background: #6478FB;
        transition:400ms ease all;
    }
    .clearAllBtn:after{
        right:inherit;
        top:inherit;
        left:0;
        bottom:0;
    }
    .clearAllBtn:hover:before,.clearAllBtn:hover:after{
        width:100%;
        transition:800ms ease all;
    }
</style>