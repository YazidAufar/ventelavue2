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
                                <tr>
                                    <td class="cart-pic first-row">
                                        <img src="assets/img/sneakers1.png" />
                                    </td>
                                    <td class="cart-title first-row text-center">
                                        Hard13 Noir
                                    </td>
                                    <td class="p-size first-row">40</td>
                                    <td class="p-price first-row">Rp. 400.000</td>
                                    <td class="delete-item-sc first-row"><a href="#"><i class='bx bx-x'></i></a></td>
                                </tr>
                                <tr>
                                    <td class="cart-pic first-row">
                                        <img src="assets/img/sneakers2.png" />
                                    </td>
                                    <td class="cart-title first-row text-center">
                                        Sang Sakerta
                                    </td>
                                    <td class="p-size first-row">41</td>
                                    <td class="p-price first-row">Rp. 430.000</td>
                                    <td class="delete-item-sc first-row"><a href="#"><i class='bx bx-x'></i></a></td>
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
                                    <input type="text" class="form-control" id="namaLengkap" aria-describedby="namaHelp" placeholder="Masukan Nama Lengkap">
                                </div>
                                <div class="form-group">
                                    <label for="namaLengkap">Alamat Email</label>
                                    <input type="email" class="form-control" id="emailAddress" aria-describedby="emailHelp" placeholder="Masukan Alamat Email">
                                </div>
                                <div class="form-group">
                                    <label for="namaLengkap">Telepon</label>
                                    <input type="text" class="form-control" id="noHP" aria-describedby="noHPHelp" placeholder="Masukan Telepon">
                                </div>
                                <div class="form-group">
                                    <label for="alamatLengkap">Alamat Lengkap</label>
                                    <textarea class="form-control" id="alamatLengkap" rows="3"></textarea>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>                  
                
                <div class="proceed-checkout">
                    <ul>
                        <li class="subtotal">ID Transaction <span>#SH12000</span></li>
                        <li class="subtotal mt-3">Subtotal <span>$240.00</span></li>
                        <li class="subtotal mt-3">Pajak <span>10%</span></li>
                        <li class="subtotal mt-3">Total Biaya <span>$440.00</span></li>
                        <li class="subtotal mt-3">Bank Transfer <span>Mandiri</span></li>
                        <li class="subtotal mt-3">No. Rekening <span>2208 1996 1403</span></li>
                        <li class="subtotal-btm mt-3">Nama Penerima <span>Yazid</span></li>
                    </ul>
                    
                    <router-link to="/success" class="proceed-btn">I ALREADY PAID</router-link>
                </div>
                    
            </div>
        </section> 
    </main>
</template>

<script>
export default {
  name: 'CartVentela',
}
</script>