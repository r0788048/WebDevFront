<template style="margin:0px">
 <div id="app" class="app" style="margin:0px"> 
  <!-- Home Pagina -->
  <Homepage v-if="page== 'home'" @change-page="goToPage" style="margin:0px" />

  <!-- Game -->
  <Gamepage v-if="page== 'game'" @change-page="goToPage"/>

  <!-- Ranking -->
  <!-- DOEN WIJ ALS TAAK VAN DIE MAN RIP ACHJA LUKT WEL ZEKERS -->
  <Rankingpage v-if="page== 'ranking'" @change-page="goToPage"/>
 </div>

</template>

<script>
//Pages
import Homepage from "./pages/Homepage.vue"
import Gamepage from "./pages/Gamepage.vue"
import Rankingpage from "./pages/Rankingpage.vue"

export default {
  name: 'App',
  components: {
    Homepage,
    Gamepage,
    Rankingpage
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