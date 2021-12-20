<template>
  <div >
    <Navigation @change-page="goToPage" />
    <h1> EuroSong Voting App </h1>
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
