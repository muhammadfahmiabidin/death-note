<template>
  <div class="list">
    <h4><label for="targetList">Masukan Target </label></h4>
    <input
      type="text"
      class="form-control"
      name="targetList"
      placeholder="Siapa yang Akan Menjadi Target?"
      v-model="target"
      @keyup.enter="tambahTarget"
    />
    <br />
    <div class="scroll">
      <table class="table" v-if="daftarTarget.length">
        <thead>
          <tr>
            <th scope="col">No</th>
            <th scope="col">Daftar Target</th>
            <th scope="col"></th>
          </tr>
        </thead>
        <tbody v-for="(target, index) in daftarTarget" :key="index">
          <td scope="row">{{ index + 1 }}</td>
          <td>{{ target }}</td>
          <td>
            <button class="btn btn-sm" @click="editTarget(index)">Edit</button>
          </td>
          <td>
            <button class="btn btn-sm" @click="hapusTarget(index)">
              Hapus
            </button>
          </td>
        </tbody>
      </table>
      <p v-else>Tidak ada target untuk saat ini</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "task1",
  data() {
    return {
      daftarTarget: [],
      target: "",
      status: false,
    };
  },
  methods: {
    tambahTarget() {
      if (this.target != null || this.target != "") {
        this.daftarTarget.push(this.target);
        this.target = "";
      }
    },
    editTarget(index) {
      this.target = prompt("Masukan Nama Target Yang Baru", "");
      if (
        this.target != null &&
        this.target != "" &&
        this.target != this.target
      ) {
        var edit = this.daftarTarget[index];
        this.daftarTarget[index] = this.target;
        console.log(edit, "telah di edit menjadi ", this.daftarTarget[index]);
        this.target = "";
      } else {
        this.target = this.daftarTarget[index];
        window.alert("masukan nama perubahan yang baru");
      }
    },
    hapusTarget(index) {
      console.log(this.daftarTarget[index], "sudah dihapus");
      this.daftarTarget.splice(index, 1);
    },
    // statusTarget(index, status) {
    //   this.status = status;
    //   if (this.status == true) {
    //     this.daftarTarget[index].strike();
    //   }
    //   console.log(this.status, this.daftarTarget[index].strike());
    // },
  },
};
</script>

<style>
@media only screen and (min-width: 128px) {
  .list {
    width: 380px;
  }
}
.list {
  background: #fbfbfb;
  border-radius: 8px;
  box-shadow: 1px 2px 8px rgba(0, 0, 0, 0.65);
  height: 480px;
  margin: 6rem auto 8.1rem auto;
  text-align: center;
}

input[type="text"] {
  width: 80%;
  padding: 5px 5px;
  margin: 5px auto;
  box-sizing: border-box;
  outline: none;
  border-radius: 10px;
  font-weight: bold;
  font-size: 14px;
}
label {
  margin-top: 15px;
  font-family: "Ralewat Thin", sans-serif;
  letter-spacing: 2px;
  padding-bottom: 4px;
  padding-top: 13px;
}
.scroll {
  height: 310px;
  overflow: auto;
}
table {
  text-align: left;
}
.btn {
  /* background: -webkit-linear-gradient(right, #eaf775, #32bd2d); */
  background: -webkit-linear-gradient(right, #4cc9f0, #4361ee);
  border: none;
  text-align: right;
  cursor: pointer;
  transition: 0.25s;
}
.btn:hover {
  box-shadow: 0px 1px 8px #7209b7;
}
</style>