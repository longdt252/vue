<template>
  <header class="header">
      <p><img src="../assets/images/logo.png"/></p>
  </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>
.header{
  height: 40px;
  background:#fafafa;
  border: 1px solid #eee;
}
.header p{
  height: 100%;
  padding: 5px;
  box-sizing: border-box;
}
.header p img{
  height: 100%;
}
</style>