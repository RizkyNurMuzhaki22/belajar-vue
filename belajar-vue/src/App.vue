<template>
  <div>
    <h1>Data Diri :</h1>
    <my-component nama="Rizky" umur="18" tanggalLahir="22/12/04" jenisKelamin="Laki-laki" agama="Islam" alamat="Kosambi"></my-component>
  </div>
</template>

<script>
import MyComponent from './MyComponent.vue';

export default {
  components: {
    MyComponent
  }
}

</script>