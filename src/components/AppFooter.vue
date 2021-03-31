<template>
  <div id="footer">
    <button @click="$emit('changePageToOne')">Мои контакты</button>
    <button @click="$emit('changePageToTwo')">Информация о контактах</button>
  </div>
</template>

<script>
export default({
  name: 'AppFooter',
})
</script>

<style scoped>
  #footer {
    display: flex;
    justify-content: space-around;
    align-items: center;
    background: #303030;
    padding: 10px 40px;
  }

  button {
    min-width: 50%;
    height: 50px;
    padding: 5px;
    background: transparent;
    color: #fff;
    outline: none;
    border: 1px solid rgba(255, 255, 255, 0.116);
    font-size: 0.6em;
  }

  button:hover {
    cursor: pointer;
    border: 1px solid rgb(255, 255, 255);
  }

  button:active {
    transform: scale(1.005);
  }
</style>