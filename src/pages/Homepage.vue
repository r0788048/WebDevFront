<template>
  <div >
    <img src="../images/logo-eurosong.png" class="logo">
    <h1 class="logo-text"> EuroSong Voting App </h1>
    <h2 class="logo-subtext"> Listen to all new songs, look at the ranking and vote your favorite one to the moon!</h2>
  </div>
</template>

<script>

export default {
    name: "Homepage",
    methods: {
        goToPage(page) {
            this.$emit("change-page", page)
        }
    }
}
</script>
