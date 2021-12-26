<template style="margin:0px">
 <div id="app" class="app" style="margin:0px"> 
   <!-- Navigation -->
  <Navigation @change-page="goToPage" style="margin:0px" />

  <!-- Home Pagina -->
  <Homepage v-if="page== 'home'" @change-page="goToPage" style="margin:0px" />

  <!-- Game -->
  <Gamepage v-if="page== 'game'" @change-page="goToPage"/>

  <!-- Ranking -->
  <Rankingpage v-if="page== 'ranking'" @change-page="goToPage"/>

  <!-- Footer -->
  <Footer />
 </div>

</template>

<script>
//Pages
import Homepage from "./pages/Homepage.vue"
import Gamepage from "./pages/Gamepage.vue"
import Rankingpage from "./pages/Rankingpage.vue"
import Navigation from "./components/Navigation.vue"
import Footer from "./components/Footer.vue"

export default {
  name: 'App',
  components: {
    Homepage,
    Gamepage,
    Rankingpage,
    Navigation,
    Footer
  },
  data() {
    return {
      page: "home"
    }
  },
  methods: {
    goToPage(page) {
      this.page = page
    }
  }
}
</script>

<style lang="scss">
  @import "./scss/style.scss";

  @font-face {
  font-family: "Gotham-Bold";
  src: local("Gotham-Bold"),
   url(./fonts/Gotham-Bold.otf) format("truetype");
  }

</style>