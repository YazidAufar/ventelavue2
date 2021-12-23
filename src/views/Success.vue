<template>
    <!--========== SUCCESS ==========-->
    <div class="animate-bottom text-centre">
        <img src="assets/img/success-buy.png" alt="" width="320">
        <h2 class="section-title">Sukses Terbayar!</h2>
        <p class="about__description">Silakan tunggu update terbaru dari kami via email yang sudah <br>Anda daftarkan sebelumnya.</p>
            
        <div class="backhome__button ">
            <router-link to="/" class="button">Back to Home</router-link>
        </div>
    </div>
</template>

<script>

export default {
  name: 'Success',
}
</script>