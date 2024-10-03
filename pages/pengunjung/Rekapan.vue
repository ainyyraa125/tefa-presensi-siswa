<template>
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <h2 class="text-center my-4"> Rekapan </h2>
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
                <td>No</td>
                <td>tanggal</td>
                <td>nama</td>
                <td>sakit</td>
                <td>hadir</td>
                <td>izin</td>
                <td>alpa</td>
                <td>Dispen</td>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(visitor, i) in visitors" :key="i">
                <td>{{ i + 1 }}</td>
                <td>{{ visitor.tanggal }}</td>
               <td>{{ visitor.siswa.nama }}</td>
                <td>{{ visitor.keterangan.keterangan }}</td>
              </tr>
            </tbody>
          </table>
        </div>
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
      .select(`*, siswa(nama), keterangan(keterangan)`)
      // .ilike("nama", `%${keyword.value}%`)
    if (data) visitors.value = data;
  };
  
  const totalpengunjung = async () => {
      const { count, error } = await supabase
      .from("Presensi")
      .select(`*, siswa(*), keterangan(*)`, {count: "exact", head: true})
    if (count) total.value = count;
  };
  
  const goBack = () => {
    window.history.back(); // Navigasi kembali ke halaman sebelumnya
  };
  
  onMounted(() => {
    getpengunjung();
    totalpengunjung();
  });
  </script>