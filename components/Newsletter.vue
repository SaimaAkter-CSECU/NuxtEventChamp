<template>
    <section id="newsletter">
        <div class="container--fluid">
            <div class="section-title text-center">
                <div class="text-h3 white--text">
                    Newsletter 
                </div>
                <div class="section-divider d-flex align-center justify-center my-9"> 
                    <v-divider class="grey"></v-divider>
                    <v-icon
                        class="mx-2"
                        color="grey"
                    >
                        mdi-email-outline
                    </v-icon>
                    <v-divider class="grey"></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div 
                        class="subtitle-1 font-weight-regular grey--text lighten-1"
                    >
                        Join our e-newsletter list to follow closely all news.
                    </div>
                </div>
            </div>
            <div class="section-content py-9">
                <v-form
                    ref="form"
                    v-model="valid"
                > 
                    <v-row class="mx-0 white--text">
                        <v-col
                            cols="12"
                            md="9"
                            sm="12"
                        >
                            <v-row class="mx-0">
                                <v-col
                                    cols="12"
                                    md="6"
                                    sm="12"
                                    class="pb-0"
                                    style="padding-bottom: 0 !important;"
                                >
                                    <v-text-field
                                        v-model="email"
                                        :rules="emailRules"
                                        label="Enter Your Email"
                                        autocomplete="off"
                                        outlined
                                        required
                                    >
                                    </v-text-field>
                                </v-col>
                                <v-col
                                    cols="12"
                                    md="6"
                                    sm="12"
                                    class="pb-0"
                                    style="padding-bottom: 0 !important;"
                                >
                                    <v-text-field
                                        v-model="name"
                                        :rules="nameRules"
                                        label="Enter Your Name"
                                        autocomplete= "off"
                                        outlined
                                        required
                                    >
                                    </v-text-field>
                                </v-col>
                                <v-col
                                    cols="12"
                                    md="6"
                                    sm="12"
                                >
                                    <v-checkbox
                                        v-model="checkbox"
                                        :rules="[v => !!v || 'You must agree to continue!']"
                                        label="I have agree to the the terms & conditions."
                                        class="white--text"
                                        color="transparent"
                                        required
                                    ></v-checkbox>
                                </v-col>
                            </v-row>
                        </v-col>
                        <v-col
                            cols="12"
                            md="3"
                            sm="12"
                        >
                            <v-btn
                                x-large
                                class="btn-yellowish-style"
                                block
                                @click="validate"
                            >
                                Submit
                            </v-btn>
                        </v-col>
                    </v-row>
                </v-form>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'Newsletter', 
        data: () => ({
            valid: true,
            name: '',
            nameRules: [
                v => !!v || 'Name is required',
            ],
            email: '',
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
            ],
            checkbox: false,
        }),

        methods: {
            validate () {
                this.$refs.form.validate(); 
            },
        },
    }
</script>