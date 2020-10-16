<template>
    <li :class="['item clearfix', todoProps.completed ? 'is-completed' : '']">
        <input type="checkbox" :checked="todoProps.completed" @change="markItemCompleted" />
        <p>{{ todoProps.title }}</p>
        <div class="btn_box clearfix">
            <button class="btn_edit btn" @click="editItem">Edit</button>
            <button class="btn_del btn" @click="deleteItem">Delete</button>
        </div>
    </li>
</template>

<script>
// import { ref } from 'vue'

export default {
    name: 'TodosListItem',
    props: ['todoProps'],
    setup(props, context){
        const markItemCompleted = () => {
            context.emit('item-completed', props.todoProps.id)
        }

        const deleteItem = () => {
             context.emit('delete-item', props.todoProps.id)
        }
        return {
            markItemCompleted,
            deleteItem
        }
    }
}
</script>

<style scoped>
    .is-completed {
        text-decoration: line-through;
    }
    .item{
        border-bottom: 1px solid #eee;
        height: 40px;
        display: flex;
        align-items: center;
        position: relative;
    }
    .item:hover{
        background: #eee!important;
    }
    .item:first-child{
        border-top: 1px solid #eee;
    }
    .item:nth-child(even){
        background: #fafafa;
    }
    .item input[type='checkbox']{
        width: 15px;
        height: 15px;
        margin-left: 10px;
    }
    .item p{
        display: inline;
        margin-left: 15px;
    }
    .item .btn_box{
        position: absolute;
        right: 10px;
    }
    .item .btn{
        padding: 5px 10px;
        border: none;
        border-radius: 3px;
        color: #fff;
    }
    .item .btn:hover{
        opacity: 0.8;
    }
    .item button.btn_del{
        background: #bf1e2e;
        margin-left: 10px;
    }
    .item button.btn_edit{
        background: #20bf1e;
    }
    .item button:hover{
        cursor: pointer;
    }
</style>