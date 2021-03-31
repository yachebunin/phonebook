<template>
  <div id="header">
    <div id="title">Контакты</div>
    <img id="logo" src="../assets/logo.png" alt="contact">
  </div>
</template>

<script> 
export default({
  name: 'AppHeader',
})
</script>

<style scoped>
  #header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #398794; 
    padding: 0px 40px;
  }

  #title {
    font-weight: 500;
    font-size: 0.8em;
  }

  #logo {
    max-width: 120px;
  }
</style>