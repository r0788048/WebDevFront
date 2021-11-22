<template>

    <div id="app">

        <Navigation />

        <h1>EuroSong Festival</h1>

        <Counter />

        <Feedback v-for="(message, index) in messages" v-bind:key="index"
          v-bind:message=message.message
          v-bind:classtype=message.classtype>
        </Feedback>

        <button @click="addMessage">
          Add Message
        </button>

    </div>

</template>

<script>
//import of the whole styling
import style from "./scss/style.scss";

//Components
import Navigation from "./components/Navigation.vue"
import Counter from "./components/Counter.vue"
import Feedback from "./components/Feedback.vue"

export default {
  name: 'App',
  components: {
    Navigation,
    Counter,
    Feedback
  },
  data() {
    return {
      messages: [
        {
          message: "Het is kapot",
          classtype: "c-feedback error"
        },
        {
          message: "Probleempje",
          classtype: "c-feedback warning"
        },
        {
          message: "Het is gelukt",
          classtype: "c-feedback success"
        }
      ]
    }
  },
  methods: {
    addMessage() {
      this.messages.push( {
        message:"NieuwItem",
        classtype:"c-feedback success"
      })
    }
  }
}
</script>