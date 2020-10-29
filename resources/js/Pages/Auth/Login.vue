<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Login</div>

                    <div class="card-body">
                        <form
                            class="mt-8 bg-white rounded-lg shadow-xl overflow-hidden"
                            @submit.prevent="submit"
                        >
                            <div class="form-group row">
                                <label
                                    for="email"
                                    class="col-md-4 col-form-label text-md-right"
                                    >Email Address</label
                                >

                                <div class="col-md-6">
                                    <input
                                        v-model="form.email"
                                        class="form-control"
                                        label="Email"
                                        type="email"
                                        autofocus
                                        autocapitalize="off"
                                    />
                                    <div id="inputEmailFeedBack">
                                        <!-- This will only be shown if the preceeding input has an invalid state -->
                                        <span
                                            style="color:red;"
                                            v-bind:key="index"
                                            v-for="(itemError,
                                            index) in errors.email"
                                            >{{ itemError }}</span
                                        >
                                    </div>
                                </div>
                            </div>
                            <div class="form-group row">
                                <label
                                    for="password"
                                    class="col-md-4 col-form-label text-md-right"
                                    >Password</label
                                >

                                <div class="col-md-6">
                                    <input
                                        v-model="form.password"
                                        class="form-control"
                                        label="Password"
                                        type="password"
                                        autofocus
                                        autocapitalize="off"
                                    />
                                    <div id="inputPasswordFeedBack">
                                        <!-- This will only be shown if the preceeding input has an invalid state -->
                                        <span
                                            style="color:red;"
                                            v-bind:key="index"
                                            v-for="(itemError,
                                            index) in errors.password"
                                            >{{ itemError }}</span
                                        >
                                    </div>
                                </div>
                            </div>
                            <div class="form-group row mb-0">
                                <div class="col-md-8 offset-md-4">
                                    <button
                                        type="submit"
                                        class="btn btn-primary"
                                    >
                                        Login
                                    </button>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Vue from "vue";
export default {
    metaInfo: { title: "Login" },
    components: {},
    props: {
        errors: Object
    },
    data() {
        return {
            sending: false,
            form: {
                email: "demo@demo.com.au",
                password: "hello2020",
                remember: null
            }
        };
    },
    // watch: {
    //     props: {
    //         // the callback will be called immediately after the start of the observation
    //         immediate: true,
    //         handler(val, oldVal) {
    //             console.log(val);
    //         }
    //     }
    // },
    methods: {
        submit() {
            const data = {
                email: this.form.email,
                password: this.form.password,
                remember: this.form.remember
            };

            this.$inertia.post("login", data, {
                onStart: () => (this.sending = true),
                onFinish: () => (this.sending = false)
            });
        }
    }
};
</script>
