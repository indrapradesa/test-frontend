<template>
  <div id="app">
    <div class="container">
      <h1 class="mb-4">Daftar User</h1>
      <hr>
      <div>
      <p>
        <b-button v-b-modal.modal-lg variant="primary">
          <b-icon icon="file-person" aria-hidden="true"></b-icon>Tambah User</b-button>

        <b-modal id="modal-lg" size="lg" title="Tambah User"> <user-form @add-user="addUser"/></b-modal>
      </p>
      </div>

      <user-table 
        v-bind:users='users' 
        @edit-user="editUser"
        @delete-user="deleteUser"
      />
    </div>
  </div>
</template>


<script>
import UserTable from '@/components/UserTable.vue'
import UserForm from '@/components/UserForm.vue'

export default {
  name: 'App',
  components: {
    UserTable,
    UserForm,
  },
  data() {
    return {
      users: [
        {
          id: 1,
          nama: 'Cristiano Ronaldo',
          ttl: '2020-01-01',
          alamat: 'Jl.Kebenaran No 10, Jawa Timur, Indonesia',
          umur : 34,
        },
        {
          id: 2,
          nama: 'Dika',
          ttl: '2020-01-03',
          alamat: 'Jl.ManggaNo 10, Jawa Timur, Indonesia',
          umur : 20,
        },
        {
          id: 3,
          nama: 'Agus',
          ttl: '2020-01-05',
          alamat: 'Jl.MataramNo 10, Jawa Timur, Indonesia',
          umur : 29,
       },
      ],
    }
  },
  methods: {
    addUser(user) {
      this.users.push(user);
    },
    editUser(id, data) {
      this.users = this.users.map(function (user) { 
        return user.id === id ? data : user;
      });
    },
    deleteUser(id) {
      this.users = this.users.filter(function (user) { 
        return user.id !== id;
      });
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top : 60px;
}
</style>
