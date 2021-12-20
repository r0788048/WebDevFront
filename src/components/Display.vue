<template>
    <div>
        Display
        <div  v-for="(song) in sorteerSongs(items)" :key="song.id">
            {{ song.artist.name }} - {{ song.title }} - {{ song.points }}
        </div>
    </div>
</template>

<script>
export default {
    name: "Display",
    props: [
        "items"
    ],
    methods: {
        sorteerSongs(songs) {
            return songs.slice().sort(function(a, b) {return b.points - a.points})
        }
    }
}
</script>