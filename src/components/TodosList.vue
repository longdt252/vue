<template>
    <ul class="listbox">
        <TodosListItem v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo"/>
    </ul>
</template>

<script>
import { ref } from 'vue'
import TodosListItem from './TodosListItem'
export default {
    name: 'TodosList',
    components: { TodosListItem },
    setup() {
        const todos = ref([
            {
                id: 1,
                title: 'Việc 1',
                completed: false
            },
            {
                id: 2,
                title: 'Việc 2',
                completed: true
            },
            {
                id: 3,
                title: 'Việc 3',
                completed: false
            },
        ])
        return {
            todos
        }
    }
}
</script>

<style>
.listbox{
    padding: 10px;
    margin: 10px;
    border: 1px solid #eee;
}
</style>