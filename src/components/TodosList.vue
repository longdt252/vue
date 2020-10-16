<template>
    <ul class="listbox">
        <AddTodo @add-todo = addTodo />
        <TodosListItem v-for="todo in todos"
                       :key="todo.id"
                       :todoProps="todo"
                       @item-completed = markComplete 
                       @delete-item = deleteComplete />
    </ul>
</template>

<script>
import { ref } from 'vue'
import axios from 'axios'

import TodosListItem from './TodosListItem'
import AddTodo from './AddTodo'

export default {
    name: 'TodosList',
    components: { TodosListItem, AddTodo },
    setup() {
        const todos = ref([])
        const getAllTodos = async () => {
            try{
                const res = await axios.get(`https://jsonplaceholder.typicode.com/todos?_limit=10`)
                todos.value = res.data
            } catch (error) {
                console.log(error);
            }
        }
        getAllTodos()
        const markComplete = id => {
            todos.value = todos.value.map(todo => {
                if (todo.id === id) todo.completed = !todo.completed;
                return todo
            })
        }

        const deleteComplete = async id => {
            try{
                await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
                todos.value = todos.value.filter(todo => todo.id !== id)
            } catch (error) {
                console.log(error);
            }
        }

        const addTodo = async newTodo => {
            try{
                const res = await axios.post(`https://jsonplaceholder.typicode.com/todos/`, newTodo)
                todos.value.push(res.data)
            } catch (error) {
                console.log(error);
            }
        }
        return {
            todos,
            markComplete,
            deleteComplete,
            addTodo
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