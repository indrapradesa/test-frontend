<template>
  <div class="user-form">
    <form @submit.prevent="submit">
      <div class="form-group">
        <label for="nama">Nama</label>
        <b-form-input v-model="user.nama" placeholder="Masukan Nama" required></b-form-input>
      </div>
      <div class="form-group">
        <label for="ttl">Tanggal Lahir</label>
        <b-form-datepicker id="example-datepicker" v-model="user.ttl" class="mb-2" required></b-form-datepicker>
      </div>
      <div class="form-group">
        <label for="alamat">Alamat</label>
        <b-col sm="10">
          <b-form-textarea
            id="textarea-small"
            size="sm"
            placeholder="Masukan Alamat"
            v-model="user.alamat" required
          ></b-form-textarea>
        </b-col>
      </div>
      <div class="form-group">
        <label for="nama">Umur:</label>
        <b-form-input type="number" v-model.number="user.umur" placeholder="Masukan Umur" min="1" required></b-form-input>
      </div>
      <b-button type="submit" variant="primary">Simpan</b-button>
      <b-button type="reset" v-b-toggle="'collapse-2'" class="m-1" variant="danger">Reset</b-button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'user-form', 
    data(){
      return {
        user: {
          nama: '',
          ttl: '',
          alamat: '',
          umur: '',
        }
      }
    },
    methods: {
      submit() {
        this.$emit('add-user', this.user)
        this.user = {
          id: '',
          nama: '',
          ttl: '',
          alamat: '',
          umur: '',
        }
      },
    },
  }
</script>
