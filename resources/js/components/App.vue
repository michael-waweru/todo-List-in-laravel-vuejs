<template>
    <div>
        <h1 style="margin-top: 200px;text-align: center">Todo List</h1>
        <div class="todoListContainer">
            <add-item-form></add-item-form>
            <list-item></list-item>
            <list-view></list-view>
        </div>
    </div>
</template>

<script>
    import addItemForm from './addItemForm'
    import listItem from './listItem'
    import listView from './listView'
    export default {
        components: {
            addItemForm,
            listView,
            listItem
        }
    }
</script>

<style scoped>
    .todoListContainer {
        width: 400px;
        margin: 50px auto auto;
    }
</style>
