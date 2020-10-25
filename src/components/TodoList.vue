<template>
    <section>
        <ul>
           <li v-for="todoItem in todoItems" v-bind:key="todoItem">{{ todoItem }}</li>
        </ul>
    </section>
</template>

<script>
    export default {
        name: "TodoList",
        data() {
            return {
                todoItems: []
            }
        },
        created() {
            if (localStorage.length > 0) {
                for (var i = 0; i < localStorage.length; i++) {
                    this.TodoItems.push(localStorage.key(i));
                }
            }
        },
    }
</script>

<style >

</style>