<template style="margin:0px">
  <div style="margin:0px">
    <Navigation @change-page="goToPage" style="margin:0px" />
    <h1> Game Page </h1>
    <Carousel :items="songs" :activeIndex="activeSongIndex" @change-index="changeActiveSongIndex"/>

    <div v-for="(votebutton, index) in votes" :key="index">
      <button  @click="vote(votebutton.points)" v-if="!votebutton.isVoted">
        Add {{ votebutton.points }} points
      </button>
      
    </div>
  
  </div>
</template>

<script>

  import Carousel from "../components/Carousel.vue"
  import Navigation from "../components/Navigation.vue"

  export default {
      name: "Gamepage",
      components: {
        Carousel,
        Navigation
      },
      data() {
        return {
          songs: [],
          activeSongIndex: 0,
          votes: [
             {
               points: 1,
               isVoted: false
             },
             {
               points: 2,
               isVoted: false
             },
             {
               points: 4,
               isVoted: false
             },
             {
               points: 8,
               isVoted: false
             }
          ]
        }
      },
      mounted() {
        console.log('mounted');
        this.fetchSongs();
      },
      methods: {
          // Navigation methodes

          goToPage(page) {
              this.$emit("change-page", page)
          },


          //Data methods

          fetchSongs() {
            // GET ALL SAUNGS
            const url = "http://webservies.be/eurosong/Songs";
            fetch(url)
              .then((response) => {
                return response.json();
              })
              .then((songs) => {
                console.log(songs);
                this.fetchArtists(songs);
              });
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

          postVote(points) {
            const songId = this.songs[this.activeSongIndex].id
            const url = "http://webservies.be/eurosong/Votes";

            fetch(
              url,
              {
                method: "POST",
                headers: {
                  'Accept': 'application/json, text/plain',
                  'Content-Type': 'application/json;charset=UTF-8'
                },
                body: JSON.stringify({
                  songID: songId,
                  points: points,
                })
              })
              .then((response) => {
                return response.json();
              })
              .then((data) => {
                console.log(data);
              });
              
          },

          //Logic methods

          changeActiveSongIndex(index) {
            this.activeSongIndex = index;
          },

          vote(points) {
            let votes = this.votes;
            votes.map((vote) => {
              if (vote.points == points) {
                vote.isVoted = true;
              }
              return vote;
            })

            // zend naar api
            this.postVote(points);

            //check of all vote afgegaan zijn
            let activeVotes = votes.filter((vote) => vote.isVoted == true)

            //als alles is gevote redirect page
            if (activeVotes.length == votes.length) {
              this.goToPage("ranking");
            }
            console.log(activeVotes);
          },

      }
  }
</script>
