<template>
    <div class="container-fluid">
      <div class="row my-5">
        <nuxt-link to="/logout">
          Logout
        </nuxt-link>
        <div class="col-lg-6">
          <nuxt-link to="/pengunjung/tambah">
            <div class="card bg-MASUK rounded-5">
              <div class="card-body">
                <h2>ABSEN MASUK</h2>
              </div>
            </div>
          </nuxt-link>
        </div>
        <div class="col-lg-6  ">
          <nuxt-link to="/pengunjung/tambah">
            <div class="card bg-KELUAR rounded-5">
              <div class="card-body">
                <h2>ABSEN KELUAR</h2>
              </div>
            </div>
          </nuxt-link>
      </div>
      <div class="col-lg-6 flex position-absolute top-100 start-50 translate-middle">
          <nuxt-link to="/pengunjung/rekapan">
            <div class="card bg-Rekapan rounded-5">
              <div class="card-body">
                <h2>Rekapan</h2>
              </div>
            </div>
          </nuxt-link>
      </div>
    </div>
  </div>
  </template>
  
  <style scoped>
  * {
    text-decoration: none;
  }
  .card {
    height: 250px;
    box-shadow: 1px 1px 10px #424242;
  }
  .card.bg-MASUK {
    margin-top: 5%;
    background-image: url("../assets/img/absen.png");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
    
  }
  .card.bg-KELUAR {
    margin-top: 5%;
    background: url("../assets/img/keluar.png");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
    
  }
  .card.bg-Rekapan {
    margin-top: 5%;
    background: url("../assets/img/Rekapan.jpeg");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
    
  }
  h2 {
    color: black;
    font: arial;
  }
  h1 {
    color: white;
  }
  .card.bg-warning {
    margin-top: 3%;
  }
  .card.bg-success {
    margin-top: 3%;
  }
  </style>