<template>
  <div class="container-fluid">
    <div class="row my-5 justify-content-evenly">
      <div class="col-lg-5 box">
        <nuxt-link to="../Pengunjung/Tambah">
          <div class="card bg-Pengunjung rounded-5">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="col-lg-5 box ">
        <nuxt-link to="../Buku">
          <div class="card bg-Buku rounded-5">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
    <div class="statistik">
      <h3><strong>STATISTIK</strong></h3>
    </div>
    <div class="Container-fluid">
    <div class="row justify-content-evenly rounded-3">
      <div class="col-5">
        <div class="card1">
          <div class="p1">
            <h1>3</h1>
            <h5>Pengunjung</h5>
          </div>
        </div>
      </div>
      <div class="col-5">
        <div class="b1">
          <h1>180</h1>
          <h5>Buku</h5>
        </div>
      </div>
    </div>
  </div>
  </div>
  
</template>

<style scoped>
.card {
    height : 250px;
    width: 105.5%;
    box-shadow: 1px 1px 10px #424242;
}
.card.bg-Pengunjung {
    background-image: url('../assets/img/PengusahaSukses.webp');
    color: black;
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
.card.bg-Buku {
    background: url('../assets/img/PengusahaSukses1.jpg') no-repeat center center;
    color: black;
    background-size: cover;
}
.card-body{
  font-family: serif;
}
.p1 {
  font-family: Arial, Helvetica, sans-serif;
  height: 250px;
  width: 105.5%;
  box-shadow: 1px 1px 10px;
  border-radius: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(221, 211, 65);
}
.b1 {
  font-family: Arial, Helvetica, sans-serif;
  height: 250px;
  width: 105.5%;
  box-shadow: 1px 1px 10px;
  border-radius: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(41, 240, 124);
}
h1{
  font-weight: bolder;
}
h5{
  padding-top: 10px;
}
.box a{
  text-decoration: none;
}
.statistik{
  padding-left: 25px;
  padding-bottom: 30px;
}
</style>