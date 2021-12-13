<template>
  <div >
    <h1> Ranking Page </h1>
    <button @click="goToPage('home')"> Show Home </button>
    <button @click="goToPage('game')"> Show Game </button>
  </div>
</template>

<script>
export default {
    name: "Gamepage",
    methods: {
        goToPage(page) {
            this.$emit("change-page", page)
        }
    }
}
</script>
