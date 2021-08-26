<template>
  <div id="app">
    <!-- Image and text -->
    <nav class="navbar navbar-light bg-primary">
      <a class="navbar-brand" href="#">
        <img src="assets/img/avataaars.svg" alt="..." width="30" height="30" class="d-inline-block align-top" />
        JotMeDown
      </a>

      <!-- <button
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
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="#">
              Home
              <span class="sr-only">(current)</span>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Features</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Pricing</a>
          </li>
          <li class="nav-item">
            <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
          </li>
        </ul>
      </div> -->
    </nav>

    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
    </div>

    <router-view />
    <!-- Footer-->
    <footer class="footer text-center">
      <div class="container">
        <div class="row">
          <!-- Footer Location-->
          <div class="col-lg-4 mb-5 mb-lg-0">
            <h4 class="text-uppercase mb-4">Location</h4>
            <p class="lead mb-0">
              310 Corporate Dr NW Suite #101,
              <br />
              Knoxville, TN 37923
            </p>
          </div>
          <!-- Footer Social Icons-->
          <div class="col-lg-4 mb-5 mb-lg-0">
            <h4 class="text-uppercase mb-4">Around the Web</h4>
            <a class="btn btn-outline-light btn-social mx-1" href="https://www.facebook.com/SidekickTherapyPartners/">
              <i class="fab fa-fw fa-facebook-f"></i>
            </a>
            <a class="btn btn-outline-light btn-social mx-1" href="https://twitter.com/sidekicktherapy/">
              <i class="fab fa-fw fa-twitter"></i>
            </a>
            <a
              class="btn btn-outline-light btn-social mx-1"
              href="https://www.linkedin.com/company/sidekicktherapypartners/"
            >
              <i class="fab fa-fw fa-linkedin-in"></i>
            </a>
          </div>
          <!-- Footer About Text-->
          <div class="col-lg-4">
            <h4 class="text-uppercase mb-4">About JotMeDown</h4>
            <p class="lead mb-0">
              JotMeDown is a note taking app made easy by Ian Iyengar for Sidekick Therapy.
              <a href="https://www.mysidekicktherapy.com/">My Sidekick Therapy</a>
              .
            </p>
          </div>
        </div>
      </div>
    </footer>
    <!-- Copyright Section-->
    <div class="copyright py-4 text-center text-white">
      <div class="container"><small>II 2021</small></div>
    </div>
  </div>
</template>

<style></style>
