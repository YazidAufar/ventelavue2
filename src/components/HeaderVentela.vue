<template>
    <!--========== HEADER ==========-->
    <header class="l-header" id="header" :class="{'dark-theme':nightMode}" >
            <b-navbar toggleable="sm" type="light" variant="light">
                
                <b-navbar-toggle target="nav-text-collapse"><i class='bx bx-menu'></i></b-navbar-toggle>

                <b-navbar-brand ><a href="#" class="nav__logo">Ventela®</a></b-navbar-brand>

                <div class="nav__shop2">
                    <a class="nav__icon">
                        <i class='bx bx-shopping-bag'></i>
                        <span>{{ keranjangUser.length }}</span>
                    </a>
                    
                    <div class="nav__shop-content">
                        <tbody v-if="keranjangUser.length > 0">
                            <div class="title_shop">
                                <span>Keranjang Belanja</span>
                            </div>

                            <div v-for="keranjang in keranjangUser" :key="keranjang.id" class="item">                       
                                <div class="image_cart">
                                    <div class="image_c">
                                        <img :src="keranjang.photo" alt="">
                                    </div>
                                </div>                     
                                <div class="description">
                                    <span>{{ keranjang.name }}</span>
                                    <span>1 Pcs</span>
                                </div>                            
                                <div class="total-price">Rp. {{ keranjang.price }}</div>
                                <a @click="removeItem(keranjang.id)" class="delete-item">
                                    <i class='bx bx-x'></i>
                                </a>
                            </div>
                            
                            <div class="total-all">
                                <span>Total</span>
                                <span>Rp. {{ totalHarga }}</span>
                            </div>
                            
                            <div class="btn-viewcard">
                                <router-link to="/ShoppingCart" class="button-top"> 
                                    View Card
                                </router-link>
                            </div>
                            
                            
                            
                            <div class="btn-checkout">
                                <a href="#" class="button-top2">Check Out</a>
                            </div> 
                        </tbody>  

                        <tbody v-else>
                            <tr>
                                <td>Keranjang kosong</td>
                            </tr>
                        </tbody>                    
                    </div>
                </div>



                <b-collapse  id="nav-text-collapse" is-nav>
                    <b-navbar-nav >
                        <ul class="nav__list">
                            <li class="nav__item"></li>
                            

                            <li class="nav__item"><router-link to="/" class="nav__link" v-scroll-to="'#home'">Home</router-link></li>
                            <li class="nav__item"><router-link to="/" class="nav__link" v-scroll-to="'#about'">About</router-link></li>
                            <li class="nav__item"><router-link to="/" class="nav__link" v-scroll-to="'#services'">Quality</router-link></li>
                            <li class="nav__item"><router-link to="/" class="nav__link" v-scroll-to="'#products'">Product</router-link></li>
                            <li class="nav__item"><router-link to="/" class="nav__link" v-scroll-to="'#size'">Size Chart</router-link></li>
                            <li class="nav__item"><router-link to="/" class="nav__link" v-scroll-to="'#contact'">Contact us</router-link></li>
                        
                            <nav>
                                <!-- <li><i class='bx bx-toggle-left change-theme' id="theme-button"></i></li> -->
                                <i class='bx bx-toggle-left change-theme' id="theme-button" v-if="nightMode" @click="nightMode = !nightMode"></i>
                                <i class='bx bx-toggle-right change-theme' id="theme-button"   v-else @click="nightMode = !nightMode"></i>
                            </nav>
                            
                            
                        </ul>
                    </b-navbar-nav>
                </b-collapse>


                <div class="nav__shop">
                    <a class="nav__icon">
                        <i class='bx bx-shopping-bag'></i>
                        <span>{{ keranjangUser.length }}</span>
                    </a>
                    
                    <div class="nav__shop-content">
                        <tbody v-if="keranjangUser.length > 0">
                            <div class="title_shop">
                                <span>Keranjang Belanja</span>
                            </div>

                            <div v-for="keranjang in keranjangUser" :key="keranjang.id" class="item">                       
                                <div class="image_cart">
                                    <div class="image_c">
                                        <img :src="keranjang.photo" alt="">
                                    </div>
                                </div>                     
                                <div class="description">
                                    <span>{{ keranjang.name }}</span>
                                    <span>1 Pcs</span>
                                </div>                            
                                <div class="total-price">Rp. {{ keranjang.price }}</div>
                                <a @click="removeItem(keranjang.id)" class="delete-item">
                                    <i class='bx bx-x'></i>
                                </a>
                            </div>
                            
                            <div class="total-all">
                                <span>Total</span>
                                <span>Rp. {{ totalHarga }}</span>
                            </div>
                            
                            <div class="btn-viewcard">
                                <router-link to="/ShoppingCart" class="button-top"> 
                                    View Card
                                </router-link>
                            </div>
                            
                            
                            
                            <div class="btn-checkout">
                                <a href="#" class="button-top2">Check Out</a>
                            </div> 
                        </tbody>  

                        <tbody v-else>
                            <tr>
                                <td>Keranjang kosong</td>
                            </tr>
                        </tbody>                    
                    </div>
                </div>  
            </b-navbar>
    </header>
</template>

<script>
export default {
    name: 'HeaderVentela',
    data() {
        return {
            nightMode: false,
            keranjangUser: []
        }
    },

    methods: {
        removeItem(idx) {
            
            // cari tahu id dari si item yang akan dihapus
            let keranjangUserStorage = JSON.parse(localStorage.getItem("keranjangUser"));
            let itemKeranjangUserStorage = keranjangUserStorage.map(itemKeranjangUserStorage => itemKeranjangUserStorage.id);
            
            //cocokan idx item dengan id yang ada di storage
            let index = itemKeranjangUserStorage.findIndex(id => id == idx);
            this.keranjangUser.splice(index, 1);

            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem("keranjangUser", parsed);
            window.location.reload();
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
    },

    computed:{
        totalHarga() {
            return this.keranjangUser.reduce(function(items, data){
                return items + data.price;
            }, 0);
        }
    },

    watch: {
        nightMode: function() {
        localStorage.setItem("nightMode", JSON.stringify(this.nightMode));
        }
    },
    created() {
        this.nightMode = JSON.parse(localStorage.getItem("nightMode"));
    }
}
</script>
