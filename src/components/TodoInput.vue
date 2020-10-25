<template>
    <div>
        <input type="text" v-model="newTodoItem">
        <button @click="addTodo">추가</button>
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
            addTodo() {
                // console.log(this.newTodoItem); 콘솔 확인용
                // input 에 입력된 데이터가 없을 경우에는 로컬 스토리지에 데이터가 저장되지 않게
                if (this.newTodoItem !== "") {
                    let value = this.newTodoItem && this.newTodoItem.trim();
                    // 입력받은 텍스트를 로컬 스토리지의 setItem() API를 이용하여 저장
                    // setItem()은 로컬 스토리지에 데이터를 추가하는 APi
                    localStorage.setItem(value, value);
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

<style >

</style>