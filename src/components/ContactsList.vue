<template>
  <div id="contacts_list">
        <contacts-item @deleteItem="deleteItem" @showItemInfo="showItemInfo" :pageOne="pageOne" :contacts="contacts"></contacts-item>
  </div>
</template>

<script>
import ContactsItem from './ContactsItem'

export default({
  name: 'ContactsList',
  props: ['contacts', 'pageOne'],
  components: {
    ContactsItem,
  },
  methods: {
    showItemInfo(index) {
      this.$emit('showItemInfo', index);
    },
    deleteItem(index) {
      this.$emit('deleteItem', index);
    }
  }
})
</script>

<style scoped>
 #contacts_list {
   display: flex;
   flex-direction: column;
   margin: 10px 40px;
 }
</style>