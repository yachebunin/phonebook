<template>
  <div id="body">
    <template v-if="pageOne">
      <contacts-list :pageOne="pageOne" :contacts="contacts"></contacts-list>
    <add-contact-window @save="save" @cancel="$emit('cancel')" :contacts="contacts" :addContactWindowActive="addContactWindowActive"></add-contact-window>
    </template>
    <template v-else>
      <contacts-list @deleteItem="deleteItem" @showItemInfo="showItemInfo" :contacts="contacts"></contacts-list>
      <add-contact-info-window @saveInfo="$emit('saveInfo')" @cancel="$emit('cancel')" :showContactInfoWindowActive="showContactInfoWindowActive" :index="index" v-if="showContactInfoWindowActive" :contacts="contacts"></add-contact-info-window>
    </template>
    <template>
      <is-agree @deleteIsAgree="$emit('deleteIsAgree')" @deleteIsNotAgree="$emit('deleteIsNotAgree')" :clearAllAgree="clearAllAgree"></is-agree>
    </template>
  </div>
</template>

<script>
import ContactsList from './ContactsList'
import AddContactWindow from './AddContactWindow'
import AddContactInfoWindow from './AddContactInfoWindow'
import IsAgree from './IsAgree'

export default({
  name: 'AppBody',
  props: ['contacts', 'addContactWindowActive', 'showContactInfoWindowActive', 'pageOne', 'index', 'clearAllAgree'],
  components: {
    ContactsList,
    AddContactWindow,
    AddContactInfoWindow,
    IsAgree,
  },
  methods: {
    save(data) {
       this.$emit('save', data)
    },
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
  #body {
    position: relative;
    min-height: 580px;
    background: #fff;
    overflow: auto;
  }
</style>