<template>
  <div >
    <Navigation @change-page="goToPage" />
    <img src="../images/logo-eurosong.png" class="logo">
    <h1 class="logo-text"> EuroSong Voting App </h1>
    <h2 class="logo-subtext"> Listen to all new songs, look at the ranking and vote your favorite one to the moon!</h2>
  </div>
</template>

<script>
import Navigation from "../components/Navigation.vue"

export default {
    name: "Homepage",
    components: {
      Navigation
    },
    methods: {
        goToPage(page) {
            this.$emit("change-page", page)
        }
    }
}
</script>
