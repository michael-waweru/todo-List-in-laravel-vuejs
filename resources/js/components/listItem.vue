<template>
    <div class="item">
        <input type="checkbox" @change="updateTodo()" v-model="item.completed">
        <span :class="['itemText', item.completed ? 'completed' : '']">{{ item.todo }}</span>
        <button class="edit">
            <font-awesome-icon icon="edit"></font-awesome-icon>
        </button>
        <button class="delete" @click="removeTodo()">
            <font-awesome-icon icon="trash"></font-awesome-icon>
        </button>

    </div>
</template>

<script>
    export default {
        name: "listItem",
        props: ['item'],
        methods: {
            updateTodo() {
                axios.post('api/todo/update/'+this.item.id, {
                    completed: this.item.completed
                }).then(response => {
                    if (response.status >= 200 && response.status <= 300) {
                        alert('The task has been updated successfully')
                        this.$emit('reloadTodos')
                    }
                })
            },
            removeTodo() {
                axios.get('api/todo/delete/'+this.item.id).then(response => {
                    if (response.status >= 200 && response.status <= 300) {
                        alert('The Task has been deleted successfully')
                        this.$emit('reloadTodos')
                    }
                })
            }
        }
    }
</script>

<style scoped>
    .item {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .completed {
        text-decoration: line-through;
        color: #999999;
    }

    .itemText {
        width: 100%;
        margin-left: 20px;
    }

    .edit {
        color: blue;
        border-radius: 5px;
        border: none;
        outline: none;
        margin-right: 5px;
        background-color: white;
        font-size: 17px;
    }

    .delete {
        color: red;
        border-radius: 5px;
        border: none;
        outline: none;
        background-color: white;
        font-size: 17px;
    }
</style>
