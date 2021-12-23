<template>
    <!--========== HOME ==========-->
    <section class="home" id="home">
         <div class="product-edit">   
            <slick ref="slick" :options="slickOptions">
                <div class="mySlides fade">
                    <div class="home__container bd-container bd-grid">
                        <div class="home__data">
                            <h1 class="home__title">Ventela Sang Sekerta Lohita</h1>
                            <h2 class="home__subtitle">Sneakers lokal hasil kolaborasi terbaik pada tahun 2020.</h2>
                            <a href="#" class="button">Explore Now</a>
                        </div>
                        <img src="assets/img/home1.png" alt="" class="home__img">
                    </div>
                </div>

                <div class="mySlides fade">
                    <div class="home__container bd-container bd-grid">
                        <div class="home__data">
                            <h1 class="home__title">Ventela Hard13 Noir</h1>
                            <h2 class="home__subtitle">Kolaborasi pertama Ventela dengan nevertoolavish.</h2>
                            <a href="#" class="button">Explore Now</a>
                        </div>
                        <img src="assets/img/home2.png" alt="" class="home__img">
                    </div>
                </div>

                <div class="mySlides fade">
                    <div class="home__container bd-container bd-grid">
                        <div class="home__data">
                            <h1 class="home__title">Ventela Armor Denim</h1>
                            <h2 class="home__subtitle">Kolaborasi dengan Badjatex menggunakan denim.</h2>
                            <a href="#" class="button">Explore Now</a>
                        </div>
                        <img src="assets/img/home3.png" alt="" class="home__img">
                    </div>
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
            slickOptions: {
                dots: true,
                infinite: true,
                speed: 300,
                slidesToShow: 1,
                adaptiveHeight: true,
                responsive: [
                    
                    {
                    breakpoint: 577,
                    settings: {
                        autoplay: true,
                        arrows: false,
                        speed: 2000,
                        autoplaySpeed: 2000,
                    }
                    }
                ]
            },
        };
    },  

  name: 'HomeVentela',
}
</script>
