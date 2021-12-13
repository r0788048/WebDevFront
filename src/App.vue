<template>
 <div id="app"> 
  <!-- Home Pagina -->
  <Homepage v-if="page== 'home'" @change-page="goToPage"/>

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
      page: "game"
    }
  },
  methods: {
    goToPage(page) {
      this.page = page
    }
  }
}
</script>