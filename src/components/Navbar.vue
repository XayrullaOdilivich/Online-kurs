<script setup>
</script>

<template>
    <nav class="navbar navbar-expand-lg bg-white p-0">
        <div class="container-fluid gx-0 position-relative">
            <div class="d-flex align-items-center ps-3 logo">
                <h1 class="m-0 fw-bold">Logo</h1>
            </div>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mx-auto mb-2 mb-lg-0 gap-3 nav-links">
                    <li class="nav-item">
                        <a class="nav-link active fw-bold" aria-current="page" href="#">Курсы</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link active fw-bold" aria-current="page" href="#">Школы</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link active fw-bold" aria-current="page" href="#">Отзывы о школах</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link active fw-bold" aria-current="page" href="#">Акции школ</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link active fw-bold" aria-current="page" href="#">Блог</a>
                    </li>
                </ul>
            </div>
            <div class="position-absolute end-60 top-0 h-100 d-flex align-items-center border-start  border-end px-3 search"
                 style="border-color: #dee2e6 !important; right: 11%">
                <img src="/assets/search.svg" alt="search" class="me-2" style="height: 50%;">
                <span class="d-none d-lg-inline">Искать курсы</span>
            </div>
            <div class="position-absolute end-60 top-0 h-100 d-flex align-items-center border-start border-light px-3 arrow"
                 style="border-color: #dee2e6 !important; right: 20%;">
                <img src="/assets/arrow.svg" alt="icon" style="height: 50%;">
            </div>
        </div>
    </nav>
</template>

<style scoped>
.navbar {
    border-bottom: 1px solid #dee2e6;
    transition: all 0.3s ease;
}

.logo {
    margin-left: 5%;
    min-width: 120px;
    transition: all 0.3s ease;
}

.nav-links {
    transition: all 0.3s ease;
    flex-wrap: nowrap;
}

.container-fluid {
    padding-left: 0 !important;
    padding-right: 0 !important;
    min-height: 60px;
}

.border-start, .border-end {
    border-width: 1px !important;
    margin-top: -1px;
    margin-bottom: -1px;
}

@media (max-width: 992px) {
    .d-none.d-lg-inline {
        display: none !important;
    }
}

@media (max-width: 1700px) {
    .arrow {
        right: 25% !important;
    }
}
@media (max-width: 1500px) {
    .logo {
        padding-left: 1rem;

    }
}
@media (max-width: 1200px) {
    .arrow {
        right: 27% !important;
    }
}
@media (max-width: 1054px) {
    .arrow {
        right: 27% !important;
    }
    .border-start, .border-end {
        border: none !important;
    }

    .search, .arrow {
        border: none !important;
        padding-left: 0.5rem !important;
        padding-right: 0.5rem !important;
    }

    .search {
        right: 40px;
    }

    .arrow {
        right: 0;
    }
}

@media (max-width: 700px) {
    .arrow {
        right: 28% !important;
    }
}
</style>
