<template>
  <div class="shopping">
    <ScrollTopVentela/>
    <HeaderVentela/>
    <CartVentela/>
    <FooterVentela/>
  </div>
</template>

<script>
import ScrollTopVentela from '@/components/ScrollTopVentela.vue';
import HeaderVentela from '@/components/HeaderVentela.vue';
import CartVentela from '@/components/CartVentela.vue';
import FooterVentela from '@/components/FooterVentela.vue';

export default {
  name: 'ShoppingCart',
  components: {
    ScrollTopVentela,
    HeaderVentela,
    CartVentela,
    FooterVentela
  }
}
</script>

