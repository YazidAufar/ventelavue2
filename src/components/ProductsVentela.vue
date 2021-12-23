<template>
    <!--========== PRODUCTS ==========-->
    <section class="products section bd-container" id="products">
        <span class="section-subtitle">Special</span>
        <h2 class="section-title">PRODUCTS of the week</h2>
        <div class="product-edit">
            <slick ref="slick" :options="slick_two" class="products__container bd-grid logo-slider">
                
                <div class="products__content">
                    <img src="assets/img/sneakers1.png" alt="" class="products__img">
                    <h3 class="products__name">Hard13 Noir</h3>
                    <span class="products__detail">Low</span><br>
                    <span class="products__preci">Rp. 400.000,-</span>
                    <a href="#" class="button products__button_detail">Detail Product</a>
                    <a href="#" class="button products__button"><i class='bx bx-cart-alt'></i></a>
                </div>

                <div class="products__content">
                    <img src="assets/img/sneakers2.png" alt="" class="products__img" >
                    <h3 class="products__name">Sang Sekerta</h3>
                    <span class="products__detail">Low</span><br>
                    <span class="products__preci">Rp. 430.000,-</span>
                    <router-link to="/product" class="button products__button_detail">Detail Product</router-link>
                    <a href="#" class="button products__button"><i class='bx bx-cart-alt'></i></a>
                </div>

                <div class="products__content">
                    <img src="assets/img/sneakers3.png" alt="" class="products__img">
                    <h3 class="products__name">P'76 Series</h3>
                    <span class="products__detail">Low</span><br>
                    <span class="products__preci">Rp. 350.000,-</span>
                    <a href="#" class="button products__button_detail">Detail Product</a>
                    <a href="#" class="button products__button"><i class='bx bx-cart-alt'></i></a>
                </div>

                <div class="products__content">
                    <img src="assets/img/sneakers4.png" alt="" class="products__img">
                    <h3 class="products__name">Urban</h3>
                    <span class="products__detail">Slip On</span><br>
                    <span class="products__preci">Rp. 300.000,-</span>
                    <a href="#" class="button products__button_detail">Detail Product</a>
                    <a href="#" class="button products__button"><i class='bx bx-cart-alt'></i></a>
                </div>
            </slick>
        </div>
    </section>
</template>

<script>
import Slick from 'vue-slick';

export default {
    components: { Slick },

    data() {
        return {
            slick_two: {
                dots: true,
                arrows: true,                
                infiniite: true,
                autoplay: true,
                speed: 2000,
                autoplaySpeed: 2000,
                responsive: [
                    {
                    breakpoint: 5000,
                    settings: {
                        slidesToShow: 3,
                        slidesToScroll: 1
                    }
                    },
                    {
                    breakpoint: 898,
                    settings: {
                        slidesToShow: 2,
                        slidesToScroll: 1
                    }
                    }
                ]
            },
        };
    },

    name: 'ProductsVentela',
}
</script>
