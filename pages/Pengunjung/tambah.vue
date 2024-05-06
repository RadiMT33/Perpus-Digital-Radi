<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <div class="kunjungan">
          <h2 class="text-center my-4">Form kunjungan</h2>
        </div>
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <input v-model="form.nama" type="text" class="nama form-control form-control-lg rounded-5" placeholder="Nama Lengkap" />
          </div>
          <div class="mb-3">
            <select v-model="form.keanggotaan" class="Keanggotaan form-control form-control-lg form-select rounded-5">
              <option value="">Keanggotaan</option>
              <option v-for="(member,i) in members" :key="i" :value="member.id">{{ member.nama }}</option>
            </select>
          </div>
          <div v-if="form.keanggotaan == 2" class="mb-3">
            <div class="row">
              <div class="col-md-4">
                <select v-model="form.tingkat" class="tingkat form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">Tingkat</option>
                  <option value="X">X</option>
                  <option value="XI">XI</option>
                  <option value="XII">XII</option>
                </select>
              </div>
              <div class="col-md-4">
                <select v-model="form.jurusan" class="jurusan form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">Jurusan</option>
                  <option value="PPLG">PPLG</option>
                  <option value="TJKT">TJKT</option>
                  <option value="TSM">TSM</option>
                  <option value="DKV">DKV</option>
                  <option value="TOI">TOI</option>
                </select>
              </div>
              <div class="col-md-4">
                <select v-model="form.kelas" class="kelas form-control form-control-lg form-select rounded-5 mb-2">
                  <option value="">Kelas</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                </select>
              </div>
            </div>
          </div>
          <div class="mb-3">
            <select v-model="form.keperluan" class="Keperluan form-control form-control-lg form-select rounded-5">                                             
              <option value="">Keperluan</option>
              <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
            </select>
          </div>
          <button type="submit" class="btn btn-lg rounded-5 px-5">Kirim</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const members = ref([]);
const objectives = ref([]);

const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
})

const kirimData = async () => {
  console.log(form.value)
  const { error } = await supabase.from("Pengunjung").insert([form.value])
  if (error) throw error
  else  navigateTo("/Pengunjung")
}

const getkeanggotaan = async () => {
  const { data, error } = await supabase.from("keanggotaan").select("*")
  if (data) members.value = data
};

const getkeperluan = async () => {
  const { data, error } = await supabase.from("keperluan").select("*")
  if (data) objectives.value = data
};

onMounted(() => {
  getkeanggotaan();
  getkeperluan();
})
</script>

<style scoped>
.btn {
  background-color: #0075FF;
  font-family: 'Times New Roman', Times, serif;
}
.nama::placeholder {
  background-color: rgb(255, 255, 255);
  font-family: 'Times New Roman', Times, serif;
  font-size: 15px;
  color: black;
}
.Keanggotaan {
  background-color: rgb(192, 192, 192);
  font-family: 'Times New Roman', Times, serif;
  font-size: 15px;
  padding-left: 15px;
}
.tingkat {
  background-color: rgb(255, 255, 255);
  font-family: 'Times New Roman', Times, serif;
  font-size: 15px;
  padding-left: 15px;
}
.jurusan {
  background-color: rgb(255, 255, 255);
  font-family: 'Times New Roman', Times, serif;
  font-size: 15px;
  padding-left: 15px;
}
.kelas {
  background-color: rgb(255, 255, 255);
  font-family: 'Times New Roman', Times, serif;
  font-size: 15px;
  padding-left: 15px;
}
.Keperluan {
  background-color: rgb(192, 192, 192);
  font-family: 'Times New Roman', Times, serif;
  font-size: 15px;
  padding-left: 15px;
}

.kunjungan {
  font-family: "Times New Roman", Times, serif;
  font-size: 15px;
}
</style>
