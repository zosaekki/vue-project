<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" @keyup.enter="addTodo" placeholder="Type what you have to do">
        <span class="addContainer" @click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                newTodoItem: ''
            }
        },
        methods: {
            addTodo() {
                if(this.newTodoItem.trim() !== '') { // 값이 있어야 함
                const value = this.newTodoItem.trim(); // trim 양쪽에 있는 빈칸을 지움
                // localStorage.setItem(value,value);
                this.$emit('childAddTodo', value);
            } else {
                this.$emit('alertModal');
            }
                this.newTodoItem = '';
            }
        }
    }
</script>

<style scoped>
    input:focus { outline: none; }
    .inputBox { 
        background-color: white; 
        height: 50px; 
        line-height: 50px; 
        border-radius: 5px; 
        display: flex;
        padding-left: 5px;
    }
    .inputBox input { 
        border-style: none; 
        font-size: 0.9rem; 
        flex-grow: 1; 
        padding: 0 10px;
    }
    .addContainer {
        background: linear-gradient(to right, #6478FB, #8763FB);
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addContainer > .addBtn { color: white; }
</style>