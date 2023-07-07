<template>
    <nav
        class="navbar navbar-expand-lg navbar-light navbar-transparent sticky-top"
        :style="`background-color: rgba(255, 255, 255, ${opacity})`"
    >
        <div class="container">
            <a class="navbar-brand" href="#">Vendre</a>
            <button
                class="navbar-toggler"
                type="button"
                data-toggle="collapse"
                data-target="#navbarNav"
                aria-controls="navbarNav"
                aria-expanded="false"
                aria-label="Toggle navigation"
            >
                <span class="navbar-toggler-icon"></span>
            </button>
            <div
                class="collapse navbar-collapse justify-content-center"
                id="navbarNav"
            >
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#">Produkt</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Partners</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Priser</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Kundcase</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Kunskap</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
    export default {
        data() {
            return {
                opacity: 0.9
            }
        }
    }
</script>

<style scoped>
    :root {
        font-family: 'Roboto', 'Open-sans', sans-serif;
        font-size: 16px;
    }
    body {
        font-family: 'Roboto', sans-serif;
    }

    .navbar-brand {
        font-weight: bold;
    }

    .nav-link {
        font-weight: 500;
    }
</style>
