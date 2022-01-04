<template>
    <!--========== PRODUCTS ==========-->
    <section class="products section bd-container" id="products">
        <span class="section-subtitle">Special</span>
        <h2 class="section-title">PRODUCTS of the week</h2>
        <div class="product-edit" v-if="products.length > 0">
            <slick ref="slick" :options="slick_two" class="products__container bd-grid logo-slider">
                <div class="products__content" v-for="itemProduct in products" v-bind:key="itemProduct.id">
                    <img v-bind:src="itemProduct.galleries[0].photo" alt="" class="products__img" >
                    <h3 class="products__name">{{ itemProduct.name }}</h3>
                    <span class="products__detail">{{ itemProduct.type }}</span><br>
                    <span class="products__preci">Rp. {{ itemProduct.price }},-</span>
                    <router-link v-bind:to="'/product/'+itemProduct.id" class="button products__button_detail">Detail Product</router-link>
                    <a @click="saveKeranjang(itemProduct.id, itemProduct.name, itemProduct.price, itemProduct.galleries[0].photo)" class="button products__button"><i class='bx bx-cart-alt'></i></a>
                                        
                </div>              
            </slick>
        </div>
        <div class="col-lg-12" v-else>
            <p>
                Produk terbaru masih belum tersedia untuk saat ini.
            </p>
        </div>
    </section>
</template>

<script>
import Slick from 'vue-slick';
import axios from "axios";

export default {
    components: { Slick },

    data() {
        return {
            products: [],

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

            keranjangUser:[]
        };
    },

    methods: {
        saveKeranjang(idProduct, nameProduct, priceProduct, photoProduct){
            var productStored = {
                id: idProduct,
                name: nameProduct,
                price: priceProduct,
                photo: photoProduct
            }
            
            this.keranjangUser.push(productStored);
            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem('keranjangUser', parsed);    

            window.location.reload();
        }
    },

    mounted(){
        axios
            .get("https://ventela.000webhostapp.com/api/products")
            .then(res => (this.products = res.data.data.data))
            .catch(err => console.log(err));
            
        
        if (localStorage.getItem ("keranjangUser")) {
            try {
                this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
            } catch (e) {
                localStorage.removeItem("keranjangUser");
            }
        }
    },

    name: 'ProductsVentela',
}
</script>
