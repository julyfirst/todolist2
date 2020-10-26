<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="할 일을 입력해 주세요" v-on:keyup.enter="addToDo">
        <span class="addContainer" v-on:click="addToDo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
    export default {
        name: "TodoInput",

        data() {
            return {
                newTodoItem: '',
            }
        },
        methods: {
            addToDo() {
                // console.log(this.newTodoItem); 콘솔 확인용
                // input 에 입력된 데이터가 없을 경우에는 로컬 스토리지에 데이터가 저장되지 않게
                if (this.newTodoItem !== "") {
                    let value = this.newTodoItem && this.newTodoItem.trim();
                    // 입력받은 텍스트를 로컬 스토리지의 setItem() API를 이용하여 저장
                    // setItem()은 로컬 스토리지에 데이터를 추가하는 APi
                    // localStorage.setItem(value, value);
                    this.$emit('addToDo', value);
                    this.clearInput();
                } else {
                    alert("입력을 해주세요!");
                }
            },
            clearInput() {
                this.newTodoItem = '';
            },
        },
    }
</script>

<style scoped>
    input:focus {
        outline: none;
    }
    .inputBox {
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>