<template>
    <form @submit="addItem">
        <input type="text" placeholder="Việc mới..." v-model="tilte"/>
        <input type="submit" value="Add" class="btn_add"/>
    </form>
</template>

<script>
import { ref } from 'vue'

export default {
    name: 'AddTodo',
    setup(props, context) {
        const tilte = ref('')
        const addItem = event => {
            event.preventDefault()
            const newItem = {
                title: tilte.value,
                completed: false
            }
            context.emit('add-todo', newItem)
            tilte.value = ''
        }
        return {
            tilte,
            addItem
        }
    }
}
</script>

<style>

</style>