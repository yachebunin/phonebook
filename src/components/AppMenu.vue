<template>
  <div id="menu">
    <button v-if="pageOne" @click="$emit('clearAll')">Удалить все</button>
    <button v-if="pageOne" @click="$emit('addContact')">Добавить +</button>
  </div>
</template>

<script>
export default({
  name: 'AppMenu',
  props: ['pageOne'],
})
</script>

<style scoped>
  #menu {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #303030;
    min-height: 50px;
  }

  button {
    min-width: 35%;
    padding: 7px 0px;
    min-height: 30px;
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