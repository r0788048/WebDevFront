<template>
  <div >
    <Navigation @change-page="goToPage" />
    <h1> Ranking Page </h1>
    <Display :items="songs"/>

  </div>
</template>

<script>
import Display from "../components/Display.vue"
import Navigation from "../components/Navigation.vue"

export default {
    name: "Gamepage",
    components: {
      Display,
      Navigation
    },
    data() {
      return {
        songs: []
      }
    },
    mounted() {
        console.log('mounted');
        this.fetchSongs();
      },
    methods: {
        goToPage(page) {
            this.$emit("change-page", page)
        },

        fetchSongs() {
            // GET ALL SAUNGS
            const url = "http://webservies.be/eurosong/Songs";
            fetch(url)
              .then((response) => {
                return response.json();
              })
              .then((songs) => {
                songs.map((song) => {
                  song.points = 0;
                  return song;
                })
                this.fetchArtists(songs);
                this.fetchVotes(songs);
              });
          },

          fetchVotes(songs) {

            // Fetch votes per song
            let counter = 0;
            songs.map((song) => {
              const url = "http://webservies.be/eurosong/Songs/" + song.id + "/points";
              fetch(url)
                .then((response) => {
                  return response.json();
                })
                .then((currpoint) => {
                    song.points = currpoint;
                    counter += 1;
                    console.log(counter);
                });
                return song;
            })

            //songs.prototype.sort(songs.points)
            songs.sort((a, b) => a.points > b.points);

            // Save data
            this.songs = songs;
            console.log(songs)
          },

          fetchArtists(songs) {
            // GET ALL ARTISTS
            const url = "http://webservies.be/eurosong/Artists";
            fetch(url)
              .then((response) => {
                return response.json();
              })
              .then((artists) => {
                songs.map((song) => {
                  // Find artist
                  const artist = artists.find((artist) => artist.id == song.artist);
                  
                  // Replace id by artist
                  song.artist = artist

                  // return new object
                  return song;
                });

              // Change data of songs and force to refresh
              this.songs = songs;
              });
          }
    }
}
</script>
