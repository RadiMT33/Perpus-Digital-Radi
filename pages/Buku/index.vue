import { NuxtLink } from '#build/components';
<template>
  <div class="container-fluid p-5">
    <div class="row">
      <div class="col-lg-12 -flex justify-content-around">
        <div class="my-5">
          <form @submit.prevent="getBuku">
            <input 
            v-model="keyword" 
            type="search" 
            class="form-control rounded-5" 
            placeholder="Mau baca apa hari ini?">
          </form>
        </div>
        <div class="my-4 text-muted">menampilkan 30 dari 30</div>
        <div class="row justify-content-evenly">
          <div v-for="(buku,i) in buku" :key="i" class="col-lg-2">
            <NuxtLink :to="`/buku/${buku.id}`">
              <div class="card mb-3">
                <div class="card-body">
                  <img :src="buku.cover" class="cover" :alt="buku.judul">
                </div>
              </div>
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
    <NuxtLink to="/">
      <button type="submit" class="btn btn-lg rounded-5 px-5">Kembali</button>
    </NuxtLink>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const buku = ref([])

const getBuku = async () => {
  const { data, error } = await supabase
  .from('buku')
  .select('*, kategori(*)')
  .ilike("judul", `%${keyword.value}%`);
  if(data) buku.value = data;
}

onMounted(() => {
  getBuku()
});

const keyword = ref("");
</script>

<style scoped>
.card-body{
  width: 100%;
  height: 400px;
  padding: 0;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
.btn{
  background-color: #ffd0d0f2;
}
.form-control{
  background-color: #ffd0d0f2;
}
</style>