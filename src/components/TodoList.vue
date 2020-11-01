<template>
    <section>
        <!-- transition-group 애니메이션 사용할 떄 쓰는 태그-->
        <transition-group name="list" tag="ul">
           <li v-for="(todoItem, index) in propsdata" class="shadow" :key="todoItem">
               <i class="checkBtn fas fa-check" aria-hidden="true"></i>
               <span @click="updateTodo(todoItem, index)">{{ todoItem }}</span>
               <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                   <i class="far fa-trash-alt" aria-hidden="true"></i>
               </span>
           </li>
        </transition-group>

       <modal-update v-if="showModalUpdate" @close="showModalUpdate = false">
            <div slot="header">
                <h3>TodolistUpdate</h3>
            </div>
            <div slot="body">
               <input type="text" v-model="todoRegItem"/>
               <span class="addContainer" v-on:click="updateTodolists">
                    <i class="addBtn fas fa-plus" aria-hidden="true"></i>
               </span>
            </div>
            <span slot="footer" @click="showModalUpdate = false">
                취소
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
       </modal-update>
    </section>
</template>

<script>
    import ModalUpdate from "./common/ModalUpdate";
    export default {
        name: "TodoList",
        components: {
            ModalUpdate: ModalUpdate
        },
        props: ['propsdata'],
        data: () =>({
            todoRegItem:'',
            showModalUpdate: false,
            index :0,
        }),
        methods: {
            removeTodo(todoItem, index) {
                this.$emit('removeTodo', todoItem, index);
            },
            updateTodo(todoItem, index) {
                console.log(todoItem, index)
                this.showModalUpdate = !this.showModalUpdate;
                this.index = index;
                this.todoRegItem = this.propsdata[index];
                console.log(this.todoRegItem)
            },
            updateTodolists() {
                if (this.todoRegItem !== "") {
                    let value = this.todoRegItem && this.todoRegItem.trim();
                    console.log("value는"+value)
                    // 입력받은 텍스트를 로컬 스토리지의 setItem() API를 이용하여 저장
                    // setItem()은 로컬 스토리지에 데이터를 추가하는 APi
                    // localStorage.setItem(value, value);
                    this.$emit('update', value, this.index);
                    this.showModalUpdate=false;
                }
            },
        },
    }
</script>

<style scoped>
    .list-enter-active, .list-leave-active {
        transition: all 1s;
    }
    .list-enter, .list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }
    ul {
        list-style: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
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
    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }

    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>