<template>
  <div id="app">
      <app-header v-once></app-header>

      <app-menu :pageOne="pageOne" @clearAll="clearContacts" @addContact="addContact"></app-menu>

      <app-body @deleteItem="deleteItem" @deleteIsNotAgree="deleteIsNotAgree" @deleteIsAgree="deleteIsAgree" @showItemInfo="showItemInfo" @saveInfo="saveInfo" @save="saveContact" @cancel="cancel" :index="index" :pageOne="pageOne" :contacts="contacts" :addContactWindowActive="addContactWindowActive" :showContactInfoWindowActive="showContactInfoWindowActive" :clearAllAgree="clearAllAgree"></app-body>

      <app-footer @changePageToTwo="changePageToTwo" @changePageToOne="changePageToOne" v-once></app-footer>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader'
import AppMenu from './components/AppMenu'
import AppBody from './components/AppBody'
import AppFooter from './components/AppFooter'

export default {
  name: 'App',
  props: [],
  components: {
    AppHeader,
    AppMenu,
    AppBody,
    AppFooter,
  },
  data() {
    return {
      contacts: [
        // {name: 'Владимир', surname: 'Маяковский',  patronymic: 'Алексеевич', number: '89145362296', index: 0},  // для примера
      ],
      addContactWindowActive: false,
      showContactInfoWindowActive: false,
      clearAllAgree: false,
      pageOne: true,
      index: 0,
    }
  },
  methods: {
    addContact() {
      this.addContactWindowActive = true;
    },
    saveContact(data) {
      this.contacts.push(
          {
            name: data.name,
            surname: data.surname,
            patronymic: data.patronymic,
            number: data.number,
            index: this.contacts.length,
            mail: '',
            adress: '',
            job: '',
          }
        );

      let contactsList = JSON.stringify(this.contacts);
      localStorage.setItem("contactsList", contactsList);

      this.addContactWindowActive = false;
    },
    clearContacts() {
      this.clearAllAgree = true;
    },
    deleteIsAgree() {
      if (this.pageOne) {
       if (localStorage.getItem("contactsList") != null) {
             localStorage.removeItem("contactsList");
          }

        this.contacts = []; 
      } else {
        this.contacts.splice(this.index, 1);

        let contactsList = JSON.stringify(this.contacts);
        localStorage.setItem("contactsList", contactsList);
      }

      this.clearAllAgree = false;
    },
    deleteIsNotAgree() {
      this.clearAllAgree = false;
    },
    deleteItem(index) {
      this.clearAllAgree = true;
      this.index = index;
    },
    cancel() {
      this.addContactWindowActive = false;
      this.showContactInfoWindowActive = false;
    },
    changePageToOne() {
      this.pageOne = true;
    },
    changePageToTwo() {
      this.pageOne = false;
    },
    showItemInfo(index) {
      this.index = index;
      this.showContactInfoWindowActive = true;
    },
    saveInfo() {
      this.showContactInfoWindowActive = false;
    },
  },
  mounted() {
    if (localStorage.getItem("contactsList") != null) {
      let contactsList = JSON.parse(localStorage.getItem("contactsList"));
        this.contacts = contactsList;
      }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap');

  * {
    margin: 0px;
    padding: 0px;
  }

  body {
    background: top / cover url('./assets/background.jpg') no-repeat fixed;
    font-family: 'Roboto', sans-serif;
    font-size: 32px;
    color: #fff;
  }

  #app {
    display: flex;
    flex-direction: column;
    max-width: 50%;
    margin: 0px auto;
  }
</style>

<style>
  @media all and (min-width: 480px) and (max-width: 900px) {
    body {
      font-size: 22px;
    }

    #app {
      max-width: 80%;
    }

    #logo {
       width: 100px;
    }
  }
</style>

<style>
  @media all and (max-width: 479px) {
    body {
      font-size: 16px;
    }

    #app {
      max-width: 80%;
    }

    #logo {
       width: 80px;
    }
  }
</style>