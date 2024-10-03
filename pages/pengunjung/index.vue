<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4"> PRESENSI SISWA</h2>
        <div class="my-3">
          <form @submit.prevent="getpengunjung">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Filter" />
          </form>
        </div>
        <div class="my-3 text-muted">
         <h3> menampilkan {{ visitors.length }} dari {{ total }}</h3>
        </div>
        <table class="table">
          <thead>
            <tr>
              <td>#</td>
              <td>TANGGAL</td>
              <td>hari</td>
              <td>NAMA</td>
              <td>KETERANGAN</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}</td>
              <td>{{ visitor.tanggal }}</td>
              <td>{{ visitor.hari.hari }}</td>
             <td>{{ visitor.siswa.nama }}</td>
              <td>{{ visitor.keterangan.keterangan }}</td>
            </tr>
          </tbody>
        </table>
      </div>
      <nuxt-link to="/pengunjung/tambah">
        <button type="submit"
                class="btn btn-lg btn-primary radius kembali">
                KEMBALI
              </button>
            </nuxt-link>
    </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const keyword = ref("");
const visitors = ref([]);
const total = ref(0);

const getpengunjung = async () => {
  const { data, error } = await supabase
    .from("Presensi")
    .select(`*, siswa(nama), keterangan(keterangan), hari(hari)`)
    // .ilike("nama", `%${keyword.value}%`)
  if (data) visitors.value = data;
};

const totalpengunjung = async () => {
    const { count, error } = await supabase
    .from("Presensi")
    .select(`*, siswa(*), keterangan(*), hari(*)`, {count: "exact", head: true})
  if (count) total.value = count;
};



onMounted(() => {
  getpengunjung();
  totalpengunjung();
});
</script>

