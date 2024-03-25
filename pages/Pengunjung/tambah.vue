<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-12">
                <h2 class="text-center my-4">ISI DATA KUNJUNGAN</h2>
                <form>
                    <div class="mb-3">
                        <form @submit.prevent="kirimData">
                        <input v-model="form.nama" type="text" placeholder="NAMA...">
                        <select v-model="form.tingkat">
                    </div>
                    <div class="mb3">
                        <div class="text">
                            <select v-model="form.Keanggotaan">
                                <option value="">KEANGGOTAAN</option>
                                <option v-for="(member, i) in members" :key="i" :value="member.id">{{member.nama}}</option>
                            </select>
                        </div>
                    </div>
                    <br>
                    <div class="mb-3">
                        <div class="row">
                            <div class="col-md-4">
                                <div class="text">
                                    <select class="form-control form-control-lg form-select rounded-5 mb-2">
                                        <option value="">Tingkat</option>
                                        <option value="X">X</option>
                                        <option value="XI">XI</option>
                                        <option value="XII">XII</option>
                                    </select>
                                </div>
                            </div>
                            <div class="col-md-4">
                                <div class="text">
                                    <select class="form-control form-control-lg form-select rounded-5 mb-2">
                                        <option value="">Jurusan</option>
                                        <option value="PPLG">PPLG</option>
                                        <option value="TJKT">TJKT</option>
                                        <option value="TSM">TSM</option>
                                        <option value="DKV">DKV</option>
                                        <option value="TOI">TOI</option>
                                    </select>
                                </div>
                            </div>                                
                            <div class="col-md-4">
                                <div class="text">
                                    <select class="form-control form-control-lg form-select rounded-5 mb-2">
                                        <option value="">Kelas</option>
                                        <option value="1">1</option>
                                        <option value="2">2</option>
                                        <option value="3">3</option>
                                        <option value="4">4</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="mb-3">
                        <div class="text">
                            <select v-model="form.Keperluan">
                                <option value="">KEPERLUAN</option>
                                <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{ item.nama}}</option>
                            </select>
                        </div>
                    </div>
                    <nuxt-link to="/Pengunjung/">
                        <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">Kirim</button>
                    </nuxt-link>
                </form>
            </div>
        </div>
    </div>
</template>
<script setup>
const supabase = useSupabaseClient()

const members = ref([])
const objectives =ref([])

const form = ref({
    nama: "",
    keanggotaan: "",
    tingkat: "",
    jurusan: "",
    kelas: "",
    keperluan: "",
})

const kirimData = async () => {
    const { error } = await supabase.from('Pengunjung').insert([form.value])
    if(!error) navigateTo('/Pengunjung')
}
const getKeanggotaan = async () => {
    const {data, error } = await supabase.from('Keanggotaan').select('*')
    if(data) members.value = data
}
const getKeperluan = async () => {
    const {data, error } = await supabase.from('Keperluan').select('*')
    if(data) objectives.value = data
}
onMounted(() => {
    getKeanggotaan()
    getKeperluan()
})
</script>

<style scoped>
.wp::-webkit-input-placeholder{
   color: black;
   font-family: "karla ital";
}
.text{
    font-family: "karla ital";
}
</style>
