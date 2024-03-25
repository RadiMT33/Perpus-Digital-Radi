<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-12">
                <h2 class="text-center my-4">ISI BUKU KUNJUNGAN</h2>
                <form>
                    <div class="mb-3">
                        <input type="text" placeholder="Nama..." class="form-control rounded-5 wp">
                    </div>
                    <div class="mb3">
                        <div class="text">
                            <select class="form-control form-control-lg form-select rounded-5">
                                <option value="">Keanggotaan</option>
                                <option value="Siswa">Siswa</option>
                                <option value="Guru">Guru</option>
                                <option value="Staf">Staf</option>
                                <option value="Umum">Umum</option>
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
                            <select class="form-control form-control-lg form-select rounded-5">
                                <option value="">Keperluan</option>
                                <option value="Baca">Baca buku</option>
                                <option value="Pinjam">Pinjam buku</option>
                                <option value="Kembalikan">Kembalikan buku</option>
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

<style scoped>
.wp::-webkit-input-placeholder{
   color: black;
   font-family: "karla ital";
}
.text{
    font-family: "karla ital";
}
</style>