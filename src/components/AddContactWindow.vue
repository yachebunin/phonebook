<template>
  <div id="add_contact_window" v-if="addContactWindowActive">
      <div id="enter_data">
        <div>Введите имя:</div>
        <input v-model="info.name">
        
        <div>Введите фамилию:</div>
        <input v-model="info.surname">

        <div>Введите отчество:</div>
        <input v-model="info.patronymic">

        <div>Введите номер:</div>
        <input v-model="info.number">

        <button @click="cancel">отмена</button>
        <button @click="save(info)">сохранить</button>
      </div>
  </div>
</template>

<script>
export default({
  name: 'AddContactWindow',
  data() {
    return {
      info: {
        name: '',
        surname: '',
        patronymic: '',
        number: '',
        index: '',
      },
    }
  },
  methods: {
    cancel() {
      this.info = {
        name: '',
        surname: '',
        patronymic: '',
        number: '',
        index: '',
      };

      this.$emit('cancel');
    },
    save(info) {
      this.$emit('save', info);

      this.info = {
        name: '',
        surname: '',
        patronymic: '',
        number: '',
        index: '',
      };
    }
  },
  props: ['addContactWindowActive', 'contacts'],
})
</script>

<style scoped>
  #add_contact_window {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0px;
    top: 0px;
    background: rgba(0, 0, 0, 0.747);
    font-size: 0.8em;
  }

  #enter_data {
    display: flex;
    flex-direction: column;
    max-width: 50%;
    align-items: center;
    text-align: center;
    margin: 20px auto;
  }

  input {
    margin-top: 10px;
    min-width: 70%;
    height: 30px;
    padding: 20px 0px;
    outline: none;
    box-sizing: border-box;
    text-align: center;
    font-size: 1em;
  }

  input:not(:last-child) {
    margin-bottom: 20px;
  }

  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  button {
    min-width: 50%;
    height: 50px;
    padding: 5px;
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