<template>
  <div>
    <h2 class="text-start my-4">{{ buku.judul }}</h2>
    <div class="row">
    <div class="col-md-5">
    <span v-if="buku.cover"><img :src="buku.cover" :alt="buku.judul"></span>
    <span v-else><img src="ManfaatBuku.jpg" :alt="buku.judul"></span>
  </div>
    <div class="col-md-6">
      <ul class="list-group list-group-flush">
        <li class="list-group-item">penulis : {{ buku.penulis }}</li>
        <li class="list-group-item">tahun_terbit : {{ buku.tahun_terbit }}</li>
        <li class="list-group-item">penerbit : {{ buku.penerbit }}</li>
        <li class="list-group-item">rak : {{ buku.rak }}</li>
        <li class="list-group-item">deskripsi : {{ buku.deskripsi }}</li>
      </ul>
    </div>
  </div>
</div>
</template>

<script setup>
const supabase = useSupabaseClient()
const route = useRoute()
const buku = ref([])

const getBukuById = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori(*)`)
  .eq('id', route.params.id)
  if(data) buku.value = data[0]
}

onMounted(() => {
  getBukuById()
})
</script>