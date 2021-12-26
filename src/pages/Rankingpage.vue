<template>
  <div >

    <Navigation @change-page="goToPage" />
    <h1 class="ranking-title"> Ranking </h1>
    <Display :items="sorteerSongs(songs)"/>
    <Footer/>

  </div>
</template>

<script>
import Display from "../components/Display.vue"
import Navigation from "../components/Navigation.vue"
import Footer from "../components/Footer.vue"

export default {
    name: "Gamepage",
    components: {
      Display,
      Navigation,
      Footer
    },
    data() {
      return {
        songs: []
      }
    },
    mounted() {
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
              });
              return song;
          })

          // Save data
          this.songs = songs;

          console.log("votesongs");
          console.log(songs);
          console.log("this.songs");
          console.log(this.songs);
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
        },

        sorteerSongs(songs) {
            return songs.slice().sort(function(a, b) {return b.points - a.points})
        }
    }
}
</script>
