<template>
    <div id="is_agree_block" v-if="clearAllAgree">
      <div id="is_agree_question">
        <div>Вы действительно хотите продолжить?</div>
        <button @click="$emit('deleteIsAgree')">Удалить</button>
        <button @click="$emit('deleteIsNotAgree')">Отмена</button>
      </div>
    </div>
</template>

<script>
export default({
  name: 'IsAgree',
  props: ['clearAllAgree'],
})
</script>

<style scoped>
  #is_agree_block {
    position: absolute;
    z-index: 1000;
    width: 100%;
    top: 0px;
    left: 0px;
    height: 100%;
    background: rgba(0, 0, 0, 0.911);
    font-size: 0.8em;
  }

  #is_agree_question {
    display: flex;
    flex-direction: column;
    max-width: 50%;
    align-items: center;
    text-align: center;
    margin: 100px auto;
  }

  button {
    min-width: 50%;
    height: 50px;
    margin-top: 20px;
    background: rgba(0, 0, 0, 0.555);
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