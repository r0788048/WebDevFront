<template>
    <div>
        <div  v-for="(song, index) in sorteerSongs(items)" :key="song.id">
            <div class="ranking-text"> #{{index+1}}: {{ song.artist.name }} by {{ song.title }} | {{ song.points }} </div>
            <iframe class="ranking-frame" :src="song.spotify" width="100%" height="100px" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
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