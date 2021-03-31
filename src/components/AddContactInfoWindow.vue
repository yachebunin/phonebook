<template>
  <div id="add_contact_info_window">
    <div id="enter_data">
        <div>Введите mail:</div>
        <input v-model="info.mail">
        
        <div>Введите адрес:</div>
        <input v-model="info.adress">

        <div>Введите job:</div>
        <input v-model="info.job">

        <button @click="cancel">отмена</button>
        <button @click="save">сохранить</button>
      </div>
  </div>
</template>

<script>
export default({
  name: 'AddContactInfoWindow',
  props: ['contacts', 'index'],
  data() {
    return {
      info: {
        mail: this.contacts[this.index].mail,
        adress: this.contacts[this.index].adress,
        job: this.contacts[this.index].job,
      },
    }
  },
  methods: {
    cancel() {
      this.$emit('cancel');
    },
    save() {
      this.contacts[this.index].mail = this.info.mail;
      this.contacts[this.index].adress = this.info.adress;
      this.contacts[this.index].job = this.info.job;

      let contactsList = JSON.stringify(this.contacts);
      localStorage.setItem("contactsList", contactsList);      

      this.$emit('saveInfo');
    }
  },
})
</script>

<style scoped>
    #add_contact_info_window {
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