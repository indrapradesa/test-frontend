<template>
<div class="user-table">
  <table class="table table-bordered ">
  <thead class="thead">
    <tr> 
      <th scope="col">Nama</th>
      <th scope="col">Tanggal Lahir</th>  
      <th scope="col">Alamat</th>
      <th scope="col">Umur</th>
      <th scope="col">Tindakan</th>
    </tr>
  </thead>
  <tbody> 
    <tr v-for="user in users" :key="user.id">
    <template v-if="userId === user.id">
      <td>
        <label for="nama" class="font-weight-bold">Nama:</label>
        <div> 
          <input type="text" v-model="user.nama" class="form-control" />
        </div>
      </td>
      <td>
        <label for="ttl" class="font-weight-bold">Tanggal Lahir:</label>
        <div> 
          <input type="date" v-model="user.ttl" class="form-control" />
        </div>
      </td>
      <td>
        <label for="alamat" class="font-weight-bold">Alamat:</label>
        <div> 
          <input type="text" v-model="user.alamat" class="form-control"  />
        </div>
      </td>
      <td>
        <label for="umur" class="font-weight-bold">Umur:</label>
        <div> 
          <input type="number" v-model="user.umur" class="form-control" min="1"  />
        </div>
      </td>
      <td> 
        <div class="mt-4">
        <button class="btn btn-success m-2" @click="saveEdit(user)">Save</button>
        <button class="btn btn-danger" @click="cancelEdit(user)" >Cancel</button>
        </div>
      </td>
    </template>
    <template v-else>
      <td>{{user.nama}}</td>
      <td>{{user.ttl}}</td>
      <td>{{user.alamat}}</td>
      <td>{{user.umur}}</td>
      <td>
        <div class="text-center">
          <b-button-group>
            <b-button variant="warning" @click="editUser(user)">
              <b-icon icon="gear-fill" aria-hidden="true"></b-icon> Edit</b-button>
            <b-button variant="danger" @click="deleteUser(user.id)">
              <b-icon icon="trash" aria-hidden="true"></b-icon> Hapus</b-button>
          </b-button-group>
        </div>
      </td>
    </template>
    <div>
  </div>
  </tr>
  </tbody>
</table>
</div>
</template>

<script>
 

  export default {
    name: 'user-table', 
    props: {
      users: Array,
    },
    data() {
      return {
          userId: null,
        }
      },
      methods: {
        editUser(user) { 
          this.data = Object.assign({}, user)
          this.userId = user.id 
          // console.log(this.data);
        },
        saveEdit(user) { 
          let id = this.data.id
          this.$emit('edit-user', id, user)  
          this.userId = null
        },
        cancelEdit(user) { 
          Object.assign(user, this.data)
          this.userId = null;
          // console.log(this.userId);
        },
        deleteUser(id){
          this.$emit('delete-user', id)  
        },
      },
  }
</script>

<style scoped> 
</style> 