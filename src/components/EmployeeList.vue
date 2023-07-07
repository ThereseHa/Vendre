<template>
    <div class="page-wrapper">
        <div class="container text-center">
            <h1 class="mb-4">Dessa stjärnor jobbar hos oss</h1>
            <div class="row">
                <div
                    class="col-md-4 col-sm-6 mb-4"
                    v-for="employee in employees"
                    :key="employee.id"
                >
                    <div class="text-center">
                        <!--Renderar ut avatar -->
                        <img
                            :src="employee.avatar"
                            alt="Profilbild"
                            class="rounded-circle mb-2 avatar"
                            width="150"
                            height="150"
                        />
                        <h4>
                            <!--Renderar namnen och mail, även en ikon för mail-->
                            {{ employee.first_name }} {{ employee.last_name }}
                        </h4>
                        <a
                            :href="'mailto:' + employee.email"
                            class="email-link"
                        >
                            <i class="bi bi-envelope-fill"></i>
                            {{ employee.email }}
                        </a>
                    </div>
                </div>
            </div>
            <!--pagination som är anpassat enligt Vendres färgtema-->
            <nav aria-label="Pagination" class="mt-4">
                <ul class="pagination justify-content-center">
                    <li
                        class="page-item"
                        v-for="page in 2"
                        :key="page"
                        :class="{ active: currentPage === page }"
                    >
                        <a
                            class="page-link"
                            href="#"
                            @click="fetchEmployees(page)"
                        >
                            {{ page }}
                        </a>
                    </li>
                </ul>
            </nav>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'

    export default {
        data() {
            return {
                employees: [],
                currentPage: 1,
                totalPages: 0
            }
        },
        mounted() {
            this.fetchEmployees(this.currentPage)
        },
        methods: {
            fetchEmployees(page) {
                axios
                    .get(`https://reqres.in/api/users?page=${page}`)
                    .then((response) => {
                        this.employees = response.data.data
                        this.currentPage = response.data.page
                        this.totalPages = response.data.total_pages
                    })
                    .catch((error) => {
                        console.error(error)
                    })
            }
        }
    }
</script>

<style>
    .container {
        padding-top: 50px;
    }

    .pagination {
        display: flex;
        justify-content: center;
    }
    .page-wrapper {
        background-image: linear-gradient(rgb(237, 235, 252), white);
        min-height: 100vh;
    }
    .pagination .page-link {
        font-family: 'Roboto', sans-serif;
        color: rgb(79, 53, 228);
        transition: color 0.3s ease;
    }

    .pagination .page-link:hover {
        color: white;
        background-color: rgb(79, 53, 228);
    }

    .pagination .page-item.active .page-link {
        background-color: rgb(79, 53, 228);
        border-color: rgb(79, 53, 228);
        color: white;
    }

    .pagination .page-item.active .page-link:hover {
        background-color: rgb(79, 53, 228);
        color: white;
    }
    .email-link {
        text-decoration: none;
    }
    .mb-4 {
        font-weight: bold;
    }
    .avatar {
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3); /* Lägger till en subtil skugga */
    }
</style>
