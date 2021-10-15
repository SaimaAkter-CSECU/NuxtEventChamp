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
                            mdi-check-decagram-outline
                        </v-icon>
                        <span class="ml-3">Thank you. Your order has beed received</span>
                    </div>

                    <div
                        class="pa-7"
                        color= "#f9f9f9" 
                        style="background-color: #f9f9f9"
                    >
                        <div>
                            <div class="subtitle-1 font-weight-bold text-uppercase">
                                order number: 
                            </div>
                            <div class="subtitle-1 font-weight-normal">
                                {{orderNo}}
                            </div>
                        </div>
                        <div>
                            <div class="subtitle-1 font-weight-bold text-uppercase">
                                date: 
                            </div>
                            <div class="subtitle-1 font-weight-normal">
                                {{date}}
                            </div>
                        </div>
                        <div>
                            <div class="subtitle-1 font-weight-bold text-uppercase">
                                total: 
                            </div>
                            <div class="subtitle-1 font-weight-normal">
                                ${{total}}
                            </div>
                        </div>
                        <div>
                            <div class="subtitle-1 font-weight-bold text-uppercase">
                                payment method: 
                            </div>
                            <div class="subtitle-1 font-weight-normal">
                                {{paymentMethod}}
                            </div>
                        </div>
                    </div>


                    <div 
                        class="cart-content pa-7"
                        color="#f9f9f9"
                    >
                        <div class="text-h4 text--uppercase mt-9 mb-7">Order Details</div>
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
                                    Total
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
                                    Payment Method
                                </div>
                            </v-col>
                            <v-col
                                col="12"
                                md="6"
                                sm="6"
                                xs="6"
                            >
                                <div class="text-p">
                                    {{paymentMethod}}
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
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'OrderReceived',
        data: () => ({
            orderNo: 2911, 
            paymentMethod: 'Direct Bank Transfer', 
            total: 259, 
            date: 'October 12, 2021', 

            subtotal: 249, 
            shipping: 10, 
            quantity: 5, 
            productTitle: 'Personal Ticket', 
            
            
             
            
        }),
        methods: {
            
        },
        mounted() {
        
        }
        
    }
</script>