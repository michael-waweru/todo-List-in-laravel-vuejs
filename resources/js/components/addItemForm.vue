<template>
    <div class="addItem">
        <input type="text" class="input" placeholder="Add a Todo task" v-model="item.name">
        <button class="addButton">
            <font-awesome-icon
                icon = "plus"
                class = "plus"
                @click="addItem()">
            </font-awesome-icon>
        </button>
    </div>
</template>

<script>
    export default {
        name: "addItemForm",
        data:function () {
            return {
                item: {
                    name: ""
                }
            }
        },
        methods: {
            addItem() {
                if (this.item.name !== '') {
                    axios.post('api/todo/store', {
                        todo: this.item.name
                    }).then(response => {
                        if (response.status >= 200 && response.status <= 300) {
                            this.item.name = null
                        }
                    })
                }
            }
        }
    }
</script>

<style scoped>
    .addItem {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 25px;
    }

    .input {
        border-style: solid;
        border-color: #3f9ae5;
        border-top-right-radius: 4px;
        border-bottom-right-radius: 4px;
        border-width: 1px;
        outline: none;
        padding: 5px;
        height: 30px;
        width: 100%;
    }

    .addButton {
        height: 42px;
        width: 50px;
        border-style: solid;
        border-color: blue;
        border-top-right-radius: 4px;
        border-bottom-right-radius: 4px;
        border-width: 1px;
        background-color: white;
        margin-left: 10px;
    }

    .plus {
        font-size: 20px;
        color: #1f6fb2;
    }
</style>
