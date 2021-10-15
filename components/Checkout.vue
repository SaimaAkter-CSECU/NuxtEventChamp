<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <div 
                class="white content-div pa-8 rounded-lg"
            >
                <div
                >
                    <div class="cart-notification-div d-flex align-center pa-6 my-7">
                        <v-icon
                            color="yellowish" 
                        >
                            mdi-ticket
                        </v-icon>
                        <span class="ml-3">Have a coupon?</span>
                    </div>

                    <div class="cart-content">
                        <div class="text-h4 text--uppercase mt-9 mb-7">Billing Details</div>
                            <v-form
                                ref="form"
                                v-model="valid"
                                lazy-validation
                            >
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="firstName"
                                            :rules="inputRules"
                                            label="First Name"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="lastName"
                                            :rules="inputRules"
                                            label="Last Name"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="12"
                                        sm="12"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="companyName"
                                            label="Company Name (Optional)"
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-select
                                            v-model="country"
                                            :items="items"
                                            :rules="[v => !!v || 'Country is required']"
                                            label="Country"
                                            required
                                            outlined
                                        ></v-select>
                                    </v-col>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-select
                                            v-model="district"
                                            :items="items2"
                                            :rules="[v => !!v || 'District is required']"
                                            label="District"
                                            required
                                            outlined
                                        ></v-select>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="town"
                                            :rules="inputRules"
                                            label="Town / City"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="postcode"
                                            :rules="inputRules"
                                            label="PostCode / Zip"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="12"
                                        sm="12"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="address"
                                            :rules="inputRules"
                                            label="Address"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="phone"
                                            :rules="inputRules"
                                            label="Phone"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                    <v-col
                                        col="12"
                                        md="6"
                                        sm="6"
                                        xs="12"
                                    >
                                        <v-text-field
                                            v-model="email"
                                            :rules="emailRules"
                                            label="Email Address"
                                            required
                                            block
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                </v-row>
                                <v-row>
                                    <v-col
                                        col="12"
                                        md="12" 
                                        sm="12"
                                        xs="12"
                                    >
                                        <v-textarea
                                            v-model="note"
                                            label="Order Notes (Optional)"
                                            rows="4"
                                            block
                                            outlined
                                        ></v-textarea>
                                    </v-col>
                                </v-row>

                                <div class="my-9">
                                    <div class="text-h4 text--uppercase mt-9 mb-7">Your order</div>
                                    <v-row
                                        style="border: 1px solid #eaeaea"
                                    >
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                            style="border-right: 1px solid #eaeaea;"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                Product
                                            </div>
                                        </v-col>

                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                Subtotal
                                            </div>
                                        </v-col>
                                    </v-row>
                                    <v-row
                                        style="border: 1px solid #eaeaea"
                                    >
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                            style="border-right: 1px solid #eaeaea;"
                                        >
                                            <div class="subtitle-1">
                                                {{productTitle}} x {{quantity}}
                                            </div>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                        >
                                            <div class="subtitle-1">
                                                ${{subtotal}}
                                            </div>
                                        </v-col>
                                    </v-row>
                                    <v-row
                                        style="border: 1px solid #eaeaea"
                                    >
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                            style="border-right: 1px solid #eaeaea"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                Subtotal
                                            </div>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                ${{subtotal}}
                                            </div>
                                        </v-col>
                                    </v-row>
                                    <v-row
                                        style="border: 1px solid #eaeaea"
                                    >
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                            style="border-right: 1px solid #eaeaea;"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                Shipping
                                            </div>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                ${{shipping}}
                                            </div>
                                        </v-col>
                                    </v-row>
                                    <v-row
                                        style="border: 1px solid #eaeaea"
                                    >
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                            style="border-right: 1px solid #eaeaea;"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                Total
                                            </div>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="6"
                                            sm="6"
                                            xs="6"
                                        >
                                            <div class="subtitle-1 font-weight-medium">
                                                ${{total}}
                                            </div>
                                        </v-col>
                                    </v-row>
                                </div>   

                                <div
                                    class="pa-7"
                                    style="background: #f9f9f9" 
                                >
                                    <v-radio-group
                                        v-model="radios"
                                        mandatory
                                    >
                                        <v-radio
                                            label="Direct Bank Transfer"
                                            value="Direct Bank Transfer"
                                        ></v-radio>
                                        <v-radio
                                            label="Check payments"
                                            value="Check payments"
                                        ></v-radio>
                                    </v-radio-group>

                                    <v-divider></v-divider>
                                    <div class="body-2">
                                        Your personal data will be used to process your order, support your experience throughout this website, and for other purposes described in our privacy policy.
                                    </div>
                                    <div class="d-flex justify-end mt-5">
                                        <NuxtLink to="OrderReceived">
                                            <v-btn 
                                                class="btn-yellowish-style mt-9"
                                                style="letter-spacing:0px;"  
                                                block
                                                x-large
                                                elevation="0"
                                            >
                                                place order
                                            </v-btn>
                                        </NuxtLink>
                                    </div> 
                                </div>      
                            </v-form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Checkout",
        data: () => ({ 
            valid: false, 
            firstName: '',
            lastName: '',
            companyName: '',
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
            country: null,
            district: null,
            town: '',
            postcode: '',
            address: '',
            phone: '',
            email: '',
            note: '', 
            paymentMethod: 'Direct Bank Transfer', 
            total: 259, 
            date: 'October 12, 2021', 
            subtotal: 249, 
            shipping: 10, 
            quantity: 5, 
            productTitle: 'Personal Ticket', 
            radios: null, 

            inputRules: [
                v => !!v || 'This Field is required',
            ],
            emailRules: [
                v => !!v || 'Email is required',
                v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
            ],
        }),
        methods: {
            validate () {
                this.$refs.form.validate()
            },
        }
    }
</script>