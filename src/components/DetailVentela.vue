<template>
    <main class="l-main">
        <!--========== PAGINATION ==========-->            
        <section class="section bd-container" id="breadcrumb">
            <div class="bd-grid breadcrumb">
                <div class="breadcrumb">
                    <li><router-link to="/"> <i class='bx bxs-home'></i>  Home</router-link></li>
                    <li>Detail</li>
                </div>
                <div class="breadcrumb-pagination">
                </div>
            </div>
        </section>    
    
        <!--========== DETAIL ==========-->
        <section class="detail bd-container" id="detail">
            <div class="detail__container  bd-grid">
                <div class="detail__img">
                   
                    <div class="product-pic-zoom">
                        <img class="product-big-img" :src="gambar_default" alt="" />
                    </div>
                    <div class="product-thumbs" v-if="productDetails.galleries.length > 0">
                        <slick ref="slick" :options="slider_nav" class="product-thumbs-track ps-slider bd-grid">
                            <div 
                                v-for="ss in productDetails.galleries"
                                :key="ss.id"
                                class="pt" 
                                @click="changeImage(ss.photo)" 
                                :class="ss.photo == gambar_default ? 'active' : ''">

                                <img :src="ss.photo" alt />
                            </div>                            
                        </slick>
                    </div>
                </div>

                <div class="detail__data">
                    <span class="section-subtitle detail__initial">{{ productDetails.type }}</span>
                    <h2 class="section-title detail__initial">{{ productDetails.name }}</h2>
                    

                    <div class="size_detail-container">
                        <b>SIZE :  </b>{{checked}}
                        <div class="sizes_detail" >
                            <input type="radio" id="36" value="36" v-model="checked">
                            <label for="36" class="size_detail" >36</label>

                            <input type="radio" id="37" value="37" v-model="checked">
                            <label for="37" class="size_detail" >37</label>

                            <input type="radio" id="38" value="38" v-model="checked">
                            <label for="38" class="size_detail" >38</label>

                            <input type="radio" id="39" value="39" v-model="checked">
                            <label for="39" class="size_detail" >39</label>

                            <input type="radio" id="40" value="40" v-model="checked">
                            <label for="40" class="size_detail" >40</label>

                            <input type="radio" id="41" value="41" v-model="checked">
                            <label for="41" class="size_detail" >41</label>

                            <input type="radio" id="42" value="42" v-model="checked">
                            <label for="42" class="size_detail" >42</label>

                            <input type="radio" id="43" value="43" v-model="checked">
                            <label for="43" class="size_detail" >43</label>

                            <input type="radio" id="44" value="44" v-model="checked">
                            <label for="44" class="size_detail" >44</label>

                            <input type="radio" id="45" value="45" v-model="checked">
                            <label for="45" class="size_detail" >45</label>
                        </div>
                    </div>   
                   
                    <p class="detail__description" v-html="productDetails.description"></p>
                    <div class="price_detail">
                        <b>Rp. {{ productDetails.price }}</b>
                    </div>
                    <br>    
                    <router-link to="/ShoppingCart">
                        <a @click="saveKeranjang(productDetails.id, productDetails.name, productDetails.price, productDetails.galleries[0].photo)" href="#" class="button">Add to Cart</a>
                    </router-link>
                </div> 
            </div>
        </section>

        <!--========== PRODUCTS ==========-->
        <section class="products section bd-container" id="products">
            <h2 class="section-title">Related Products</h2>
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
        
    </main>
</template>

<script>
import Slick from 'vue-slick';

import axios from "axios";

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

            slider_nav: {
                infinite: true,
                slidesToShow: 3,
                slidesToScroll: 3,
            },

            
            checked: '',

            gambar_default: "",
            productDetails: [],
            keranjangUser:[]
        };
    },

    methods: {
        changeImage(urlImage){
            this.gambar_default = urlImage;
        },
        setDataPicture(data) {
            // replace object productDetails dengan data dari API
            this.productDetails = data;
            // replace value gambar default dengan data dari API (galleries)
            this.gambar_default = data.galleries[0].photo;
        },
        saveKeranjang(idProduct, nameProduct, priceProduct, photoProduct){
            var productStored = {
                "id": idProduct,
                "name": nameProduct,
                "price": priceProduct,
                "photo": photoProduct
            }
            
            this.keranjangUser.push(productStored);
            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem('keranjangUser', parsed);    
        }
    },

    mounted(){
        if (localStorage.getItem('keranjangUser')) {
            try{
                this.keranjangUser = JSON.parse(localStorage.getItem('keranjangUser'));
            } catch(e) {
                localStorage.removeItem('keranjangUser');
            }    

        }
        
        axios
            .get("https://ventela.000webhostapp.com/api/products", {
                params: {
                    id: this.$route.params.id
                }    
            })
            .then(res => (this.setDataPicture(res.data.data)))
            // eslint-disable-next-line no-console
            .catch(err => console.log(err));
    },
    
    name: 'DetailVentela',
}
</script>
