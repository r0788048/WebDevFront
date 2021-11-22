<template>
  <div id="app">
    <nav class="c-nav">
      <ul class="c-nav-list">
        <li class="c-nav-list-item">
          Home
        </li>
        <li class="c-nav-list-item">
          Contact
        </li>
        <li class="c-nav-list-item">
          Vote
        </li>
      </ul>
    </nav>

    <h1>EuroSong Festival</h1>

    <div class="c-feedback error">
      "Het is kapot"
    </div>

    <div class="c-feedback warning">
      "Error message"
    </div>

    <div class="c-feedback success">
      "Het is niet kapot"
    </div>

  </div>
</template>

<script>
//import of the whole styling
import style from "./scss/style.scss";

export default {
  name: 'App'
}
</script>