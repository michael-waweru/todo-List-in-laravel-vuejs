<template>
   <div>
       <div v-for="(item,index) in items" :key="index">
           <list-item
               :item = "item"
               v-on:reloadTodos="getTodos()"
               class="item">
           </list-item>
       </div>
   </div>
</template>

<script>
    import listItem from "./listItem";
    export default {
        name: "listView",
        components: {
            listItem
        },
        data: function () {
            return {
                items: []
            }
        },
        methods: {
            getTodos() {
                axios.get('api/todos').then(response => {
                    if (response.status === 200) {
                        this.items = response.data.todos
                    }
                })
            }
        },
        created() {
            this.getTodos()
        }
    }
</script>

<style scoped>
    .item {
        padding: 12px;
        margin-top: 5px;
        border-style: solid;
        border-color: blue;
        border-radius: 7px;
        border-width: 1px;
    }
</style>
