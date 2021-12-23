<template>
    <!--========== HEADER ==========-->
    <header class="l-header" id="header" :class="{'dark-theme':nightMode}" >
            <b-navbar toggleable="sm" type="light" variant="light">
                
                <b-navbar-toggle target="nav-text-collapse"><i class='bx bx-menu'></i></b-navbar-toggle>

                <b-navbar-brand ><a href="#" class="nav__logo">Ventela®</a></b-navbar-brand>

                <div class="nav__shop2">
                    <a href="#" class="nav__icon">
                        <i class='bx bx-shopping-bag'></i>
                        <span>2</span>
                    </a>
                    
                    <div class="nav__shop2-content">
                        
                        <div class="title_shop">
                            <span>Keranjang Belanja</span>
                        </div>
                    
                        <div class="item">                       
                            <div class="image_cart">
                                <div class="image_c">
                                    <img src="assets/img/sneakers1.png" alt="">
                                </div>
                            </div>                     
                            <div class="description">
                                <span>Hard13 Noir</span>
                                <span>1 Pcs</span>
                            </div>                            
                            <div class="total-price">Rp. 400.000</div>
                            <a href="#" class="delete-item">
                                <i class='bx bx-x'></i>
                            </a>
                        </div>
        
                        <div class="item">                       
                            <div class="image_cart">
                                <div class="image_c">
                                    <img src="assets/img/sneakers2.png" alt="">
                                </div>
                            </div>                       
                            <div class="description">
                                <span>Sang Sakerta</span>
                                <span>1 Pcs</span>
                            </div>                        
                            <div class="total-price">Rp. 430.000</div>
                            <a href="#" class="delete-item">
                                <i class='bx bx-x'></i>
                            </a>
                        </div>
                        <div class="total-all">
                            <span>Total</span>
                            <span>Rp. 830.000</span>
                        </div>
                        <div class="btn-viewcard">
                            <a href="#" class="button-top">View Card</a>
                        </div>
                        <div class="btn-checkout">
                            <a href="#" class="button-top2">Check Out</a>
                        </div>                        
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
                    <a href="#" class="nav__icon">
                        <i class='bx bx-shopping-bag'></i>
                        <span>2</span>
                    </a>
                    
                    <div class="nav__shop-content">
                        
                        <div class="title_shop">
                            <span>Keranjang Belanja</span>
                        </div>
                    
                        <div class="item">                       
                            <div class="image_cart">
                                <div class="image_c">
                                    <img src="assets/img/sneakers1.png" alt="">
                                </div>
                            </div>                     
                            <div class="description">
                                <span>Hard13 Noir</span>
                                <span>1 Pcs</span>
                            </div>                            
                            <div class="total-price">Rp. 400.000</div>
                            <a href="#" class="delete-item">
                                <i class='bx bx-x'></i>
                            </a>
                        </div>
        
                        <div class="item">                       
                            <div class="image_cart">
                                <div class="image_c">
                                    <img src="assets/img/sneakers2.png" alt="">
                                </div>
                            </div>                       
                            <div class="description">
                                <span>Sang Sakerta</span>
                                <span>1 Pcs</span>
                            </div>                        
                            <div class="total-price">Rp. 430.000</div>
                            <a href="#" class="delete-item">
                                <i class='bx bx-x'></i>
                            </a>
                        </div>
                        <div class="total-all">
                            <span>Total</span>
                            <span>Rp. 830.000</span>
                        </div>
                        <div class="btn-viewcard">
                            <a href="#" class="button-top">View Card</a>
                        </div>
                        <div class="btn-checkout">
                            <a href="#" class="button-top2">Check Out</a>
                        </div>                        
                    </div>
                </div>  
            </b-navbar>
    </header>
</template>

<script>
export default {
    name: 'HeaderVentela',
    data: () => {
        return {
        nightMode: false
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
