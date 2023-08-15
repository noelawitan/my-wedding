<template>
  <nav :class="['navbar', 'navbar-expand-lg', 'fixed-top', isSticky ? 'sticky' : '']">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Noel & Claire</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText"
              aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse text-end float-end" id="navbarText">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="#">Our Story</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">When and where</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Faq</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Rsvp</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Contact</a>
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
      isSticky: false,
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isSticky = window.scrollY > 50; // You can adjust this value
    },
  },
};
</script>
<style scoped>
.navbar {
  background: transparent !important;
  font-family: 'Great Vibes', cursive; /* Apply the font to the entire navbar */
}

.navbar-nav .nav-link {
  font-size: 1.2rem; /* Match the paragraph size from your full-screen image */
  margin: 0.2rem 0; /* Apply the same margin as well */
}

/* Add some additional styling to ensure a smooth appearance */
.navbar-toggler-icon {
  background-color: #FFF; /* Adjust as needed to match your site's color scheme */
}

.navbar-nav .nav-link.active {
  font-weight: bold; /* Add bold to the active link to make it stand out */
}

.navbar {
  transition: all 0.3s ease; /* Smooth transition */
}

.sticky {
  background-color: black !important;
  color: white !important;
  z-index: 1000; /* Ensure navbar is above other content */
}

.sticky .nav-link {
  color: white !important;
}

.sticky .navbar-toggler-icon {
  background-color: white !important;
}
</style>