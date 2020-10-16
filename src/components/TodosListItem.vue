<template>
    <li :class="['item clearfix', todoProps.completed ? 'is-completed' : '']">
        <input type="checkbox" :checked="todoProps.completed" />
        <p>{{ todoProps.title }}</p>
        <button class="btn_del">Delete</button>
    </li>
</template>

<script>
import { ref } from 'vue'

export default {
    name: 'TodosListItem',
    props: ['todoProps'],
    setup(){
        const newId = ref('my-id2')
        return {
            newId
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
    .item button.btn_del{
        position: absolute;
        right: 10px;
        padding: 5px 10px;
        background: #bf1e2e;
        border: none;
        border-radius: 3px;
        color: #fff;
    }
    .item button:hover{
        cursor: pointer;
    }
</style>