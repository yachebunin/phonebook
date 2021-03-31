<template>
  <div id="contacts_list_info">
    <contacts-list-info @deleteItem="$emit('deleteItem')" :contacts="contacts"></contacts-list-info>
  </div>
</template>

<script>
import ContactsList from './ContactsList'

export default({
  name: 'ContactsListInfo',
  props: ['contacts'],
  components: {
    ContactsList,
  }
})
</script>

<style scoped>
#contacts_list_info {
    position: relative;
    min-height: 580px;
    padding: 10px 40px;
    background: #fff;
    overflow: auto;
    color: #000;
  }
</style>