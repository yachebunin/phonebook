<template>
  <ul>
    <li class="contacts_item" v-for="(contact, index) in contacts" :key="index" :id="index">
      <div>{{contact.name}} {{contact.surname}} {{contact.patronymic}}</div>
      <div id="contacts_item_number">{{contact.number}}</div>
      <button v-if="!pageOne" @click="showItemInfo">( i )</button>
      <button v-if="!pageOne" id="deleteItem" @click="deleteItem">&#10005;</button>
    </li>
  </ul>
</template>

<script>
export default({
  name: 'ContactsItem',
  props: ['contacts', 'pageOne'],
  methods: {
    deleteItem(event) {
      let index = event.target.parentElement.id;

      this.$emit('deleteItem', index);
    },
    showItemInfo(event) {
      let index = event.target.parentElement.id;

      this.$emit('showItemInfo', index)
    }
  }
})
</script>

<style scoped>
  #contacts_list .contacts_item:nth-child(odd) {
    background-color: #296d79;
  }

  .contacts_item {
    display: grid;
    align-items: center;
    grid-template: auto / auto auto auto auto;
    margin-bottom: 10px;
    padding: 5px;
    border-radius: 5px;
    background: #398794;
    font-size: 0.7em;
  }

  .contacts_item {
    margin-bottom: 10px;
    padding: 10px;
  }
  
  #contacts_item_number {
    padding-left: 20px;
    margin-right: 20px;
    overflow: auto;
  }

  button {
    height: 40px;
    padding: 5px;
    background: transparent;
    color: #fff;
    font-weight: bold;
    outline: none;
    border: 1px solid rgba(255, 255, 255, 0.116);
  }
  
  button:hover {
    cursor: pointer;
    background: #303030;
  }

  button:active {
    transform: scale(1.005);
  }
</style>