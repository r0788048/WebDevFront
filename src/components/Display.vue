<template>
    <div>
        <br>
        <div  v-for="(song, index) in items" :key="song.id">
            <div v-if="index < 3">
                <div class="podium-text"> #{{index+1}}: {{ song.title }} by {{ song.artist.name }} </div><div class="podium-points"> {{ song.points }} Points</div>
                <iframe v-if="index == 0" class="ranking-frame" :src="song.spotify" width="100%" height="500px" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
                <iframe v-if="index > 0" class="ranking-frame" :src="song.spotify" width="100%" height="300px" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
            </div>
            <div v-if="index > 2">
                <div class="ranking-text"> #{{index+1}}: {{ song.title }} by {{ song.artist.name }} </div><div class="ranking-points"> {{ song.points }} Points </div>
                <iframe class="ranking-frame" :src="song.spotify" width="100%" height="80px" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"></iframe>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Display",
    props: [
        "items"
    ]
}
</script>