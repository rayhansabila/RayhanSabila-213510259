<template>
  <div>
    <h1>Daftar Mata Kuliah Kelas 4A</h1>
    <form @submit.prevent="tambahMataKuliah">
      <input type="text" placeholder="Nama Mata Kuliah" v-model="namaMataKuliah">
      <button type="submit">Tambah</button>
    </form>
    <ul>
      <li v-for="(mataKuliah, index) in mataKuliahList" :key="index">
        <input type="checkbox" v-model="mataKuliah.selesai">
        <span :class="{ 'coret': mataKuliah.selesai }">{{ mataKuliah.nama }}</span>
        <button @click="hapusMataKuliah(index)">Hapus</button>
      </li>
    </ul>
    <div>
      <label for="filter">Filter:</label>
      <input type="text" id="filter" v-model="filterMataKuliah">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      namaMataKuliah: '',
      filterMataKuliah: '',
      mataKuliahList: []
    }
  },
  methods: {
    tambahMataKuliah() {
      if (this.namaMataKuliah) {
        this.mataKuliahList.push({
          nama: this.namaMataKuliah,
          selesai: false
        });
        this.namaMataKuliah = '';
      }
    },
    hapusMataKuliah(index) {
      this.mataKuliahList.splice(index, 1);
    }
  },
  computed: {
    mataKuliahListFiltered() {
      return this.mataKuliahList.filter(mataKuliah => mataKuliah.nama.toLowerCase().includes(this.filterMataKuliah.toLowerCase()));
    }
  }
}
</script>

<style scoped>
.coret {
  text-decoration: line-through;
}
</style>

<style>

body {
  font-family: Arial, sans-serif;
  background-color: #091839;
  margin: 0;
  padding: 0;
}


/* Style untuk elemen h1 */
h1 {
  font-size: 24px;
  font-weight: bold;
}

/* Style untuk form */
form {
  margin-bottom: 20px;
}

/* Style untuk input */
input[type="text"] {
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ffffff;
  margin-right: 10px;
}

/* Style untuk tombol tambah */
button[type="submit"] {
  padding: 8px;
  background-color: #0d00c6;
  color: white;
  border-radius: 4px;
  border: none;
  cursor: pointer;
}

/* Style untuk elemen ul */
ul {
  list-style-type: none;
  padding: 0;
}

/* Style untuk li */
li {
  margin-bottom: 10px;
}

/* Style untuk checkbox */
input[type="checkbox"] {
  margin-right: 10px;
}

/* Style untuk span nama mata kuliah */
span {
  font-size: 16px;
}

/* Style untuk tombol hapus */
button {
  padding: 5px;
  background-color: #f44336;
  color: white;
  border-radius: 4px;
  border: none;
  cursor: pointer;
}

/* Style untuk filter label */
label[for="filter"] {
  margin-right: 10px;
}

/* Style untuk filter input */
#filter {
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

</style>



<style>

  
  #app {
    background-color: #150a0a;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  h1 {
    text-align: center;
    color: #08c6f1;
  }
  
  form {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  label {
    font-weight: bold;
    color: #00bfff;
  }
  
  input[type="text"] {
    padding: 10px;
    margin: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
    font-size: 16px;
  }
  
  button[type="submit"] {
    padding: 10px 20px;
    margin: 5px;
    border: none;
    border-radius: 5px;
    background-color: #007bff;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
  }
  
  button[type="submit"]:hover {
    background-color: #0069d9;
  }
  
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  li {
    display: flex;
    align-items: center;
    margin: 10px;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #05de75;
    background-color: #fff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  li label {
    margin-left: 10px;
    font-size: 16px;
    color: #333;
  }
  
  li button {
    margin-left: auto;
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    background-color: #dc3545;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
  }
  
  li button:hover {
    background-color: #c82333;
  }
  
  input[type="checkbox"] {
    display: none;
  }
  
  input[type="checkbox"] + label:before {
    content: "\2714";
    display: inline-block;
    margin-right: 10px;
    font-size: 20px;
    color: #ccc;
  }
  
  input[type="checkbox"]:checked + label:before {
    color: #007bff;
  }
  
</style>