<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <p class="addBtn">add</p>
            <!-- <i class="fa-solid fa-plus"></i> -->
        </span>

        <modal v-if="showModal" @close="showModal = false">
            <template v-slot:header>
                <i class="closeModalBtn fas fa-times-circle" v-on:click="showModal = false">경고!</i>
            </template>
            <template v-slot:body>아무것도 입력하지 않았습니다.</template>
            <!-- <template v-slot:footer>copy right</template> -->
        </modal>
    </div>
</template>

<script>
import Modal from './common/AlertModal.vue';

export default {
    name: 'TodoInput',

    data: function() {
        return {
            newTodoItem: "",
            showModal: false
        };
    },
    methods: {
        addTodo: function() {
            if (this.newTodoItem !== ''){
                this.$emit('addTodoItem', this.newTodoItem);
                this.clearInput();
            } else {
                this.showModal = !this.showModal;
            }
        },
        clearInput: function() {
            this.newTodoItem = '';
        }
    },
    components: {
        Modal: Modal
    }
};
</script>

<style scoped>
input:focus {
    outline: none;
}
.inputBox input{
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
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn {
    color: white;
    vertical-align: middle;
}
.closeModalBtn {
    color: #42b983;
}
</style>