<template>
  <div class="shopping">
    <ScrollTopVentela/>
    <HeaderVentela/>
    <DetailVentela/>
    <FooterVentela/>
  </div>
</template>

<script>
import ScrollTopVentela from '@/components/ScrollTopVentela.vue';
import HeaderVentela from '@/components/HeaderVentela.vue';
import DetailVentela from '@/components/DetailVentela.vue';
import FooterVentela from '@/components/FooterVentela.vue';

export default {
  name: 'Product',
  components: {
    ScrollTopVentela,
    HeaderVentela,
    DetailVentela,
    FooterVentela
  }
}
</script>

