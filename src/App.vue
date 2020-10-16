<template>
  <div>
    <Header/>
    <TodosList/>
  </div>
</template>

<script>
import Header from './components/Header'
import TodosList from './components/TodosList'
export default {
  name: 'App',
  components: { Header, TodosList }
}
</script>

<style>
@import './assets/css/base.css';
</style>
