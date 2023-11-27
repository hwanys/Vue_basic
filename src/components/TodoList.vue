<template>
    <div>
        <ul>
            <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
                <input type="checkbox" class="checkBtn fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.completed}" 
                    v-on:click="toggleComplete(todoItem, index)">
                <span v-bind:class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
                <span class="removeBtn" @click="removeTodo(todoItem, index)">
                    <button class="BtnColor">삭제</button>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
export default { 
    name: 'TodoList',
    props: ['propsdata'],
    methods: {
        removeTodo: function(todoItem, index) {
            this.$emit('removeItem', todoItem, index);
        },
        toggleComplete: function(todoItem, index) {
            this.$emit('toggleItem', todoItem, index);
        }
    }
};
</script>

<style scoped>
ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
}
li {
    display: flex;
    min-height: 0px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
}
.removeBtn {
    margin-left: auto;
}
.BtnColor {
    background-color: #de4343;
    border-color: #de4343;
    color: white;
}
.checkBtn {
    zoom: 0.18;
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
}   
.checkBtnCompleted {
    color: #b3adad;
}
.textCompleted {
    text-decoration: line-through;
    color: #b3adad
}
</style>