<template>
    <div>
        <!-- <button class="prev-song" @click="changeIndex(-1)"> Previous Song </button> -->
        <img class="prev-song" src="../images/prev.png" @click="changeIndex(-1)">
        <div v-for="(song, index) in items" :key="song.id">
            <div class="song-middle" v-if="index == activeIndex">
                <div class="game-text">{{ song.title }} by {{ song.artist.name }}</div>
                <iframe class="game-frame" :src="song.spotify" width="80%" height="380" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
            </div>
        </div>
        <!-- <button class="next-song" @click="changeIndex(1)"> Next Song </button> -->
        <img class="next-song" src="../images/next.png" @click="changeIndex(1)">
        <div class="reset-float"></div>
    </div>
</template>

<script>
export default {
    name: "Carousel",
    props: [
        "items",
        "activeIndex"
    ],
    methods: {
        changeIndex(value) {
            // copieke gemaakt want ge kunt waarden ni direct aanpassen
            let index = this.activeIndex;

            //gecheckt op einde of begin van lijst --> cirkelke
            index += value;
            if (index < 0) {
                index = this.items.length - 1;
            } else if (index == this.items.length) {
                index = 0;
            }

            console.log(index);
            this.$emit("change-index", index)
        }
    }
}
</script>