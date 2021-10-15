<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <div 
                class="white content-div pa-8 rounded-lg"
            >
                <div
                    v-if="checkCart == null"
                >
                    <div class="cart-notification-div empty-cart d-flex align-center pa-6 my-7">
                        <v-icon
                            color="yellowish" 
                        >
                            mdi-cart-off
                        </v-icon>
                        <span class="ml-3">Your cart is currently empty.</span>
                    </div>
                    <NuxtLink to="../../Events/">
                        <v-btn
                            class="btn-yellowish-style"
                            x-large
                            elevation="0"
                        >
                            Return to Shop
                        </v-btn>
                    </NuxtLink>
                </div>
                <div
                    v-else
                >
                    <div class="cart-notification-div d-flex align-center pa-6 my-7">
                        <v-icon
                            color="yellowish" 
                        >
                            mdi-cart-plus
                        </v-icon>
                        <span class="ml-3">Product Added to You Cart Successfully.</span>
                    </div>

                    <div class="cart-content pb-9">
                        <v-simple-table
                        >
                            <thead
                            >
                                <tr>
                                    <th></th>
                                    <th></th>
                                    <th>Product</th>
                                    <th>Price</th> 
                                    <th>Quantity</th>
                                    <th>Subtotal</th> 
                                </tr>
                            </thead>
                            <tbody>
                                <tr
                                    v-for="product in productList" 
                                    :key="product.id"
                                >
                                    <td>
                                        <span
                                            style="cursor: pointer;"                                            
                                            @click="removeItemFromCart()"
                                        >
                                            x
                                        </span>
                                    </td>
                                    <td>
                                        <v-img
                                            :src="product.url"
                                            width="50px"
                                        ></v-img>
                                    </td>
                                    <td>{{product.title}}</td>
                                    <td>{{product.price}}</td>
                                    <td>{{product.quantity}}
                                        <!-- <v-text-field
                                            v-model="quantity"
                                            :value="product.quantity" 
                                            type="number"
                                            outlined
                                        ></v-text-field> -->
                                    </td>
                                    <td>{{product.price * product.quantity}}</td>
                                </tr>
                                <tr>
                                    <td colspan="6" >
                                        <div class="d-flex align-center flex-wrap">
                                            <div class="d-flex align-center justify-space-between">
                                                <v-text-field
                                                    v-model="coupon"
                                                    label="Coupon Code"
                                                    outlined
                                                ></v-text-field>
                                                <v-btn
                                                    class="ml-2 btn-yellowish-style rounded-md"
                                                    @click="checkcouponCode()"
                                                    elevation="0"
                                                    x-large 
                                                >
                                                    apply coupon
                                                </v-btn>
                                            </div>
                                            <v-spacer></v-spacer>
                                            <div class="">
                                                <v-btn
                                                    class="ml-2 btn-yellowish-style rounded-md"
                                                    @click="updateCart()"
                                                    elevation="0"
                                                    x-large 
                                                >
                                                    Update cart
                                                </v-btn>
                                            </div>
                                        </div>
                                    </td>
                                </tr>
                            </tbody>
                        </v-simple-table>
                    </div>
                    <div class="cart-content">
                        <div class="text-h4 text--uppercase mt-9 mb-7">Cart Total</div>
                        <v-row
                            style="border: 1px solid #eaeaea"
                        >
                            <v-col
                                col="12"
                                md="2"
                                sm="3"
                                xs="12"
                            >
                                <div class="subtitle-1">
                                    Subtotal
                                </div>
                            </v-col>
                            <v-col
                                col="12"
                                md="10"
                                sm="9"
                                xs="12"
                            >
                                <div class="text-p">
                                    ${{subtotal}}
                                </div>
                            </v-col>
                        </v-row>
                        <v-row
                            style="border: 1px solid #eaeaea"
                        >
                            <v-col
                                col="12"
                                md="2"
                                sm="3"
                                xs="12"
                            >
                                <div class="subtitle-1">
                                    Shipping
                                </div>
                            </v-col>
                            <v-col
                                col="12"
                                md="10"
                                sm="9"
                                xs="12"
                            >
                                <div class="text-p">
                                    Flat rate: <span class="subtitle-1 font-weight-medium">${{shippingCharge}}</span>
                                </div>
                                <div class="text-p">
                                    Shipping to: <span class="subtitle-1 font-weight-medium">{{shippingAddress}}</span>
                                </div>
                                <div class="text-p">
                                    <v-btn
                                        text
                                        style="letter-spacing: 0px" 
                                        class="px-0"
                                        @click="changeShippingAddress = !changeShippingAddress"
                                    >
                                        Change Address 
                                        <span>
                                            <v-icon>
                                                mdi-truck-cargo-container
                                            </v-icon>
                                        </span>
                                    </v-btn>
                                </div>

                                <div 
                                    class="my-9 pa-5"
                                    v-show="changeShippingAddress"
                                >
                                    <v-form
                                        ref="form"
                                        v-model="valid"
                                        lazy-validation
                                    >
                                        <v-select
                                            v-model="country"
                                            :items="items"
                                            :rules="[v => !!v || 'Country is required']"
                                            label="Country"
                                            required
                                            outlined
                                        ></v-select>
                                        <v-select
                                            v-model="state"
                                            :items="items2"
                                            :rules="[v => !!v || 'State is required']"
                                            label="District"
                                            required
                                            outlined
                                        ></v-select>
                                        <v-text-field
                                            v-model="town"
                                            :rules="inputRules"
                                            label="Town / City"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                        <v-text-field
                                            v-model="postcode"
                                            :rules="inputRules"
                                            label="PostCode / Zip"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                        <v-btn
                                            :disabled="!valid"
                                            class="my-5 mr-4 btn-yellowish-style rounded-md"
                                            @click="changeAddress(), changeShippingAddress = false"
                                            elevation="0"
                                            x-large 
                                        >
                                            Update
                                        </v-btn>
                                    </v-form>
                                </div>
                            </v-col>
                        </v-row>
                        <v-row
                            style="border: 1px solid #eaeaea"
                        >
                            <v-col
                                col="12"
                                md="2"
                                sm="3"
                                xs="12"
                            >
                                <div class="subtitle-1">
                                    Total
                                </div>
                            </v-col>
                            <v-col
                                col="12"
                                md="10"
                                sm="9"
                                xs="12"
                            >
                                <div class="subtitle-1 font-weight-medium">
                                    ${{subtotal + shippingCharge}}
                                </div>
                            </v-col>
                        </v-row>
                        <v-row>
                            <v-col
                                cols="12"
                                md="12"
                                xs="12"
                            >
                                <NuxtLink to="Cart/Checkout">
                                    <v-btn 
                                        class="btn-yellowish-style mt-9"
                                        style="letter-spacing:0px;" 
                                        block
                                        x-large
                                        elevation="0"
                                    >
                                        proceed to checkout
                                    </v-btn>
                                </NuxtLink>
                            </v-col>
                        </v-row>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Cart',
        data: () => ({
            checkCart: '',
            changeShippingAddress: false, 
            productList: [
                {
                    id: 1,
                    title: 'Personal Ticket',
                    price: 29, 
                    quantity: 2, 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-1-300x300.jpg',
                },
                {
                    id: 2,
                    title: 'Business Ticket',
                    price: 59, 
                    quantity: 3, 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-1-300x300.jpg',
                },
            ],
            subtotal: '',
            shippingCharge: 10, 
            coupon: '', 
            valid: false, 
            shippingAddress: 'Atlanta',
            town: '',
            postcode: '', 
            inputRules: [
                v => !!v || 'This Field is required',
            ],
            country: null,
            state: null,  
            items: [
                'Item 1',
                'Item 2',
                'Item 3',
                'Item 4',
            ],
            items2: [
                'Item 1',
                'Item 2',
                'Item 3',
                'Item 4',
            ],
        }),
        methods: {
            async checkcouponCode(){
                console.log('checkcouponCode'); 
            },
            async updateCart(){
                console.log('updateCart'); 
            },
            async removeItemFromCart(){
                console.log('removeItemFromCart');
            },
            async changeAddress () {
                this.$refs.form.validate()
            },
        },
        mounted() {
            this.checkCart = localStorage.getItem('cart'); 
            console.log(this.checkCart);

            let productSubtotal = this.productList.map(x => x.quantity * x.price);
            console.log(productSubtotal);
            this.subtotal = productSubtotal.reduce((x, y) => x + y);
            console.log(this.subtotal);
        }
        
    }
</script>