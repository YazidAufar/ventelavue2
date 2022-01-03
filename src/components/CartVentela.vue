<template>
    <main class="l-main">
        <!--========== PAGINATION ==========-->            
        <section class="section bd-container" id="breadcrumb">
            <div class="bd-grid breadcrumb">
                <div class="breadcrumb">
                    <li><router-link to="/"> <i class='bx bxs-home'></i>  Home</router-link></li>
                    <li>Shopping Cart</li>
                </div>
                <div class="breadcrumb-pagination">
                </div>
            </div>
        </section>    

        <!--========== CART ==========-->
        <section class="cart bd-container" id="cart">
            <div class="cart__container bd-grid">
                <div class="shopping-cart">
                    <div class="cart-table">
                        <table>
                            <thead>
                                <tr>
                                    <th>Image</th>
                                    <th class="p-name text-center">Product Name</th>
                                    <th>Size</th>
                                    <th>Price</th>
                                    <th>Action</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="keranjang in keranjangUser" :key="keranjang.id">
                                    <td class="cart-pic first-row">
                                        <img :src="keranjang.photo" >
                                    </td>
                                    <td class="cart-title first-row text-center">
                                        {{ keranjang.name }}
                                    </td>
                                    <td class="p-size first-row">40</td>
                                    <td class="p-price first-row">{{ keranjang.price }}</td>                                    
                                    <td @click="removeItem(keranjang.id)" class="delete-item-sc first-row"><i class='bx bx-x'></i></td>
                                </tr>
                                
                            </tbody>
                        </table>
                    </div>

                    <div class="col-lg-8">
                        <h3 class="mb-4">
                            Informasi Pembeli:
                        </h3>
                        <div class="user-checkout">
                            <form>
                                <div class="form-group">
                                    <label for="namaLengkap">Nama Lengkap</label>
                                    <input 
                                        type="text" 
                                        class="form-control" 
                                        id="namaLengkap" 
                                        aria-describedby="namaHelp" 
                                        placeholder="Masukan Nama Lengkap"
                                        v-model="customerInfo.name"
                                    >
                                </div>
                                <div class="form-group">
                                    <label for="namaLengkap">Alamat Email</label>
                                    <input 
                                        type="email" 
                                        class="form-control" 
                                        id="emailAddress" 
                                        aria-describedby="emailHelp" 
                                        placeholder="Masukan Alamat Email"
                                        v-model="customerInfo.email"
                                    >
                                </div>
                                <div class="form-group">
                                    <label for="namaLengkap">Telepon</label>
                                    <input 
                                        type="text" 
                                        class="form-control" 
                                        id="noHP" 
                                        aria-describedby="noHPHelp" 
                                        placeholder="Masukan Telepon"
                                        v-model="customerInfo.number"
                                    >
                                </div>
                                <div class="form-group">
                                    <label for="alamatLengkap">Alamat Lengkap</label>
                                    <textarea 
                                        class="form-control" 
                                        id="alamatLengkap" 
                                        rows="3"
                                        v-model="customerInfo.address">
                                    </textarea>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>                  
                
                <div class="proceed-checkout">
                    <ul>
                        <li class="subtotal">ID Transaction <span>#SH12000</span></li>
                        <li class="subtotal mt-3">Subtotal <span>Rp. {{ totalHarga }}</span></li>
                        <li class="subtotal mt-3">Pajak <span>10% Rp. {{ ditambahPajak }}</span></li>
                        <li class="subtotal mt-3">Total Biaya <span>Rp. {{ totalBiaya }}</span></li>
                        <li class="subtotal mt-3">Bank Transfer <span>Mandiri</span></li>
                        <li class="subtotal mt-3">No. Rekening <span>2208 1996 1403</span></li>
                        <li class="subtotal-btm mt-3">Nama Penerima <span>Yazid</span></li>
                    </ul>
                    
                    <a @click="checkout()" href="#" class="proceed-btn">I ALREADY PAID</a>
                </div>
                    
            </div>
        </section> 
    </main>
</template>

<script>
import axios from "axios";

export default {
    name: 'CartVentela',
    data() {
        return {
            keranjangUser: [],
            customerInfo: {
                name: '',
                email: '',
                number: '',
                address: ''
            }
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
        },

        // fungsi mengirim data ke API
        checkout(){
            let productIds = this.keranjangUser.map(function(product){
                return product.id
            });

            let checkoutData = {
                'name': this.customerInfo.name,
                'email': this.customerInfo.email,
                'number': this.customerInfo.number,
                'address': this.customerInfo.address,
                "transaction_total": this.totalBiaya,
                "transaction_status": "PENDING",
                "transaction_details": productIds
            };

            axios
                .post(
                "http://ventela.000webhostapp.com/api/checkout",
                checkoutData
                )
                .then(() => this.$router.push("success"))
                // eslint-disable-next-line no-console
                .catch(err => console.log(err));
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
        },

        ditambahPajak(){
            return (this.totalHarga * 10) / 100;
        },

        totalBiaya(){
            return this.totalHarga + this.ditambahPajak;
        }
    }
}
</script>