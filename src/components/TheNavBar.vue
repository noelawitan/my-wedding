<template>
  <nav :class="['navbar', 'navbar-expand-lg', 'fixed-top', isSticky ? 'sticky' : '']">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img :src="brandLogoImg" :alt="brandLogoImg" style="width:auto;height:50px;"/>
      </a>
      <button class="navbar-toggler" type="button"
              @click="toggleCollapseNavBar"
              aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation" ref="navbarToggler">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse text-end float-end" id="navbarText" ref="navbarMenu">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="#ourStorySection" @click="collapseNavbar">Our Story</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#weddingAttireSection" @click="collapseNavbar">Attire</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#whenAndWhereSection" @click="collapseNavbar">When & Where</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="https://www.noelandclaire.com/rsvp/public/event/123" target="_self">Rsvp</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="mailto:noel.awitan@gmail.com">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
import BrandLogoImg from '@/assets/brand-logo.png';
import {Collapse} from 'bootstrap';

export default {
  data() {
    return {
      brandLogoImg: BrandLogoImg,
      collapse: null,
      isSticky: false,
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.collapse = new Collapse(this.$refs.navbarMenu, {toggle: false});
    this.$refs.navbarMenu.addEventListener('show.bs.collapse', this.setNavbarBlack);
    this.$refs.navbarMenu.addEventListener('hide.bs.collapse', this.removeNavbarBlack);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);

    this.$refs.navbarMenu.removeEventListener('show.bs.collapse', this.setNavbarBlack);
    this.$refs.navbarMenu.removeEventListener('hide.bs.collapse', this.removeNavbarBlack);
  },
  methods: {
    handleScroll() {
      this.isSticky = window.scrollY > 50;
    },
    setNavbarBlack() {
      this.isSticky = true;
    },
    removeNavbarBlack() {
      this.isSticky = window.scrollY > 50;
    },
    collapseNavbar() {
      const navbarMenu = this.$refs.navbarMenu;
      if (navbarMenu && window.getComputedStyle(navbarMenu).display !== 'none') {
        this.collapse.hide();
      }
    },
    toggleCollapseNavBar() {
      this.collapse.toggle();
    }
  },
};
</script>
<style scoped>
.navbar {
  background: transparent !important;
  font-family: 'Great Vibes', cursive;
}

.navbar-nav .nav-link {
  font-size: 1.2rem;
  margin: 0.2rem 0;
}

.navbar-toggler-icon {
  background-color: #FFF;
}

.navbar-nav .nav-link.active {
  font-weight: bold;
}

.navbar {
  transition: all 0.3s ease;
}

.sticky {
  background-color: #000 !important;
  color: white !important;
  z-index: 1000;
}

.sticky .nav-link {
  color: white !important;
}

.sticky .navbar-toggler-icon {
  background-color: white !important;
}
</style>