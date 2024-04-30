<template>
  <div class="container-fluid">
    <div class="row my-5 d-flex justify-content-evenly ">
      <div class="col-lg-6 box">
        <NuxtLink to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </NuxtLink>
      </div>
      <div class="col-lg-6 box">
        <NuxtLink to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2>Buku</h2>
            </div>
          </div>
        </NuxtLink>
      </div>
    </div>
    <div class="statistik">
      <h1>STATISTIK</h1>
    </div>
      <div class="row my-5 d-flex justify-content-evenly ">
        <div class="col-lg-6 box">
          <div class="card b2 rounded-5">
            <div class="card-body text">
              <h1 class="no">5</h1>
              <h3 class="pt-4">Pengunjung</h3>
            </div>
          </div>
        </div>
        <div class="col-lg-6 box">
          <div class="card b3 rounded-5">
            <div class="card-body text">
              <h1 class="no">30</h1>
              <h3 class="pt-4">Buku</h3>
            </div>
          </div>
        </div>
      </div>
      <div class="container">
        <div class="row">
          <Statistik />
        </div>
      </div>
    </div>
  </template>

<script setup>
useHead({ title: "Home / PERPUSTAKAAN DIGITAL" })
</script>

<style scoped>
.card {
  height: 250px;
}
.card.bg-pengunjung{
  background-image: url('../assets/img/bg-hom-pengunjung.jpeg');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: black;
}
.card.bg-buku {
  background: url('../assets/img/bg-home-perpus.jpeg') no-repeat center center;
  background-size: cover;
  color: black;
}
.statistik {
  color: rgba(181, 74, 74, 0.761);
  margin-left: 50px;
}
.box{
  width: 45%;
}
.box a{
  text-decoration: none;
}
.b2{
  background-color: #ffd0d0f2;
}
.b3{
  background-color: rgba(181, 74, 74, 0.761);
}
.text{
  display: flex;
  justify-content: center;
  align-items: center;
}
.no{
  font-size: 70px;
}
</style>