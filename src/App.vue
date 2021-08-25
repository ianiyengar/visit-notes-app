<template>
  <div id="app">
    <!-- Header-->
    <header class="masthead bg-primary text-white text-center">
      <div class="container d-flex align-items-center flex-column">
        <!-- Masthead Avatar Image-->
        <img class="masthead-avatar mb-5" src="assets/img/avataaars.svg" alt="..." />
        <!-- Masthead Heading-->
        <h1 class="masthead-heading text-uppercase mb-0">JotMeDown</h1>
        <!-- Icon Divider-->
        <div class="divider-custom divider-light">
          <div class="divider-custom-line"></div>
          <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
          <div class="divider-custom-line"></div>
        </div>
        <!-- Masthead Subheading-->
        <p class="masthead-subheading font-weight-light mb-0">A Note Taking App For Therapists</p>
      </div>
    </header>

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
