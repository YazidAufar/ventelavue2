<template>
  <div class="home" >
    <ScrollTopVentela/>
    <HeaderVentela/>
    <main class="l-main">      
      <HomeVentela/>
      <AboutVentela/>
      <ServicesVentela/>
      <ProductsVentela/>
      <SizeVentela/>
      <ContactVentela/>
    </main>
    <FooterVentela/>
  </div>
</template>

<script>
import ScrollTopVentela from '@/components/ScrollTopVentela.vue';
import HeaderVentela from '@/components/HeaderVentela.vue';
import HomeVentela from '@/components/HomeVentela.vue';
import AboutVentela from '@/components/AboutVentela.vue';
import ServicesVentela from '@/components/ServicesVentela.vue';
import ProductsVentela from '@/components/ProductsVentela.vue';
import SizeVentela from '@/components/SizeVentela.vue';
import ContactVentela from '@/components/ContactVentela.vue';
import FooterVentela from '@/components/FooterVentela.vue';

export default {
  name: 'Home',
  components: {
    ScrollTopVentela,
    HeaderVentela,
    HomeVentela,
    AboutVentela,
    ServicesVentela,
    ProductsVentela,
    SizeVentela,
    ContactVentela,
    FooterVentela
  }
}
</script>
