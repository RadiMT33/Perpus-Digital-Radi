<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <input type="search" class="form-control form-control-lg rounded-5" placeholder="Filter..." />
        </div>
        <div class="my-3 text-muted">Menampilkan 1 dari 1</div>
        <table class="table table-bordered">
          <thead>
            <tr align="center">
              <th>NO</th>
              <th>NAMA</th>
              <th>KEANGGOTAAN</th>
              <th>TINGKAT</th>
              <th>JURUSAN</th>
              <th>KELAS</th>
              <th>WAKTU</th>
              <th>KEPERLUAN</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}.</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tingkat }}</td>
              <td>{{ visitor.jurusan }}</td>
              <td>{{ visitor.kelas }}</td>
              <td>{{ visitor.tanggal }}, {{ visitor.Waktu }}</td>
              <td>{{ visitor.keperluan.nama }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <NuxtLink to="/Pengunjung/tambah">
      <button type="submit" class="btn btn-lg rounded-5 px-5">Kembali</button>
    </NuxtLink>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();

const visitors = ref([]);

const getPengunjung = async () => {
  const { data, error } = await supabase.from("Pengunjung").select(`*, keanggotaan(*), keperluan(*)`);
  if (data) visitors.value = data
}

onMounted(() => {
  getPengunjung()
})
</script>

<style scoped>
.btn {
  background-color: #faee70f2;
}
.form-control {
  background-color: #6c1313f2;
}
</style>
