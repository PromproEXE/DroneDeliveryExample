<template>
  <nav class="navbar navbar-expand-lg bg-light">
    <div class="container-fluid">
      <a class="navbar-brand d-flex align-items-end" href="/">
      <img src="/src/assets/img/delivery.png" class="me-2" alt="icon">
      <h4 class="fw-bold mb-0">FOODDY Drone</h4>
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="w-100 mx-5">
        <div class="form-control py-1 px-3 d-flex align-items-center">
            <small class="text-muted"><i class="fa-solid fa-magnifying-glass"></i></small>
                    <input
          type="text"
          class="custom-form-control w-100 ms-2"
          id="searchBar"
          placeholder="ค้นหาที่นี่"
        />
        </div>

      </div>
      <div>
        <button class="btn d-flex align-items-center">
          <img src="../assets/img/user.png" alt="profile" class="me-3" />
          <div class="d-flex align-items-center">
            <h5 class="text-capitalize mb-0 fw-bold">Promproexe</h5>
            <small class="text-muted"><i class="fa-solid fa-chevron-down ms-2"></i></small>
          </div>
        </button>
      </div>
    </div>
  </nav>
</template>
