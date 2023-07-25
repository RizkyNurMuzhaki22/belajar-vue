<template>
    <div>
      <h2>Nama : {{ nama }}! </h2>
      <p>Tanggal lahir : {{ tanggalLahir }} </p>
      <p>Jenis kelamin : {{ jenisKelamin }} </p>
      <p>Agama : {{ agama }} </p>
      <p>Alamat : {{ alamat }} </p>
      <h2 v-if="umur >= 18">Selamat datang, {{ nama }}!</h2>
    <p v-else>Maaf, kamu belum cukup umur.</p>
    <h4>List Hewan:</h4>
    <ul>
      <li v-for="hewan in daftarHewan" :key="hewan.id">{{ hewan.nama }}</li>
    </ul>
    <p v-if="daftarHewan.length === 0">Belum ada hewan.</p>
    <h2>Formulir Kontak</h2>
    <form @submit.prevent="submitForm">
      <label for="nama">Nama:</label>
      <input type="text" id="nama" v-model="kontak.nama" required>

      <label for="email">Email:</label>
      <input type="email" id="email" v-model="kontak.email" required>

      <button type="submit">Kirim</button>
    </form>
    <h2>Formulir Pendaftaran</h2>
    <form @submit.prevent="submitForm">
      <label for="username">Username:</label>
      <input type="text" id="username" v-model="user.username" :class="{ 'is-invalid': isInvalidUsername }" required>
      <div v-if="isInvalidUsername" class="error-message">Username harus terdiri dari 6 karakter atau lebih.</div>

      <label for="password">Password:</label>
      <input type="password" id="password" v-model="user.password" :class="{ 'is-invalid': isInvalidPassword }" required>
      <div v-if="isInvalidPassword" class="error-message">Password harus terdiri dari 8 karakter atau lebih.</div>

      <button type="submit">Daftar</button>
    </form>
    </div>
  </template>
  
  <script>
  export default{
    props: ['nama', 'umur' , 'tanggalLahir' , 'jenisKelamin' , 'agama' ,
  'alamat'],
    data() {
    return {
      daftarHewan: [
        { id: 1, nama: 'Kucing' },
        { id: 2, nama: 'Anjing' },
        { id: 3, nama: 'Kelinci' },
      ],
       kontak: {
        nama: '',
        email: '',
      },
      user: {
        username: '',
        password: '',
      },
    };
  },
  computed: {
    isInvalidUsername() {
      return this.user.username.length < 6;
    },
    isInvalidPassword() {
      return this.user.password.length < 8;
    },
  },
  methods: {
    submitForm() {
      // Lakukan sesuatu dengan data user
      console.log(this.user);
    },
  },

  methods: {
    submitForm() {
      // Lakukan sesuatu dengan data kontak
      console.log(this.kontak);
    }
  }
}
  </script>
  <style>
  .error-message {
    color: red;
    margin-top: 5px;
  }
  .is-invalid {
    border-color: red;
  }
  </style>
  
  <!-- Props itu kaya jembatan buat nyambungin data dari komponen satu ke komponen lain. 
    Data itu dimasukin di komponen induk dan bisa diakses sama komponen anak. 
    Jadi bisa transfer data dengan mudah dan lancar. -->