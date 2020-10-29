<template>
    <div class="container">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Navbar</a>
            <button
                class="navbar-toggler"
                type="button"
                data-toggle="collapse"
                data-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent"
                aria-expanded="false"
                aria-label="Toggle navigation"
            >
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#" v-on:click="logout">
                            Logout
                        </a>
                    </li>
                </ul>
            </div>
        </nav>
        <div class="d-flex justify-content-center align-self-center">
            Dashboard Page Goes Here
        </div>
    </div>
</template>

<script>
import Vue from "vue";
export default {
    metaInfo: { title: "Dashboard" },
    methods: {
        logout() {
            this.$inertia.post("logout");
        }
    }
};
</script>
