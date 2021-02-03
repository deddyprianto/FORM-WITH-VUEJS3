<template>
  <p>pesan sekarang</p>
  <form class="form" @submit.prevent="submiit">
    <label>Masukkan Nama Anda</label>
    <input type="text" v-model="nama" />

    <label>Masukkan Nama Buku Yg anda Pilih</label>
    <input type="text" v-model="buku" />

    <label>Role: </label>
    <select v-model="role">
      <option value="buku PHP">Book Of PHP</option>
      <option value="buku Java">Book Of Java</option>
    </select>

    <label for=""
      >masukkan jenis buku yg ingin anda sarankan pisahkan dengan tanda
      koma</label
    >
    <input type="text" v-model="tempatPenampungan" @keyup="tekankeyboard" />

    <div class="data">
      <p :key="jeniss" v-for="jeniss in jenis" class="pill">
        {{ jeniss }}
      </p>
    </div>
    <div class="tombol">
      <button class="button">Kirim Pesanan</button>
    </div>
  </form>

  <div v-if="isSubmitted" class="container">
    <h3>Detail Pesanan Anda</h3>
    <div class="card">
      <ul>
        <li>Nama: {{ nama }}</li>
        <li>Nama Buku: {{ buku }}</li>
        <li>Judul buku: {{ role }}</li>
        <li>
          Request Buku untuk dihadirkan:
          <p :key="data" v-for="data in jenis">
            {{ data }}
          </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nama: "",
      buku: "",
      role: "",
      tempatPenampungan: "",
      jenis: [],
      isSubmitted: false,
    };
  },
  methods: {
    tekankeyboard(e) {
      if (e.key === "," && this.tempatPenampungan) {
        if (!this.jenis.includes(this.tempatPenampungan)) {
          this.jenis.push(this.tempatPenampungan);
        }
        this.tempatPenampungan = "";
      }
    },
    submiit() {
      this.isSubmitted = true;
    },
  },
};
</script>

<style>
.container {
  margin-top: -100px !important;
  width: 40%;
  background-color: white;
  margin: 20px auto;
  border-radius: 20px;
  transition: 0.3s;
  animation: deddy 2s ease-in-out forwards;
}
@keyframes deddy {
  from {
    transform: translateY(0);
    opacity: 0;
  }
  to {
    transform: translateY(100px);
    opacity: 1;
  }
}
.container .card ul {
  list-style: none;
}
.card > ul > li:last-child {
  margin-top: 20px;
}
.form {
  max-width: 420px;
  margin: 30px auto;
  background-color: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
.data {
  display: flex;
  flex-wrap: wrap;
}
.term {
  margin-top: 2em;
  display: flex;
  align-items: center;
}
.term p {
  font-size: 17px;
}
.term > input[type="checkbox"] {
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.tombol {
  margin-top: 20px;
  width: 100%;
  display: flex;
  justify-content: center;
}
.button {
  width: 50%;
  background-color: lightblue;
  height: 40px;
  border-radius: 20px;
  border: none;
  line-height: 40px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background-color: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
</style>
