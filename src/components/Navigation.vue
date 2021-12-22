<template>

    <nav class="c-nav" v-bind:id="id" v-if="shownavigation">
        <div class="nav-left">
            <ul class="c-nav-list">

                <li class="c-nav-list-item" v-for="(link, index) in links" v-bind:key="index">

                    <a @click="goToPage(link.linkUrl)">

                        {{ link.linkText }}

                    </a>

                </li>

            </ul>
        </div>
        <div class="nav-right">
            <ul class="c-nav-list">

                 <li class="c-nav-list-item">
                    <a @click="alertUser()">
                        Search
                    </a>
                </li>
                <li class="c-nav-list-item">
                    <a @click="alertUser()">
                        Login
                    </a>
                </li>

            </ul>
        </div>
    </nav>

</template>

<script>
    export default {
        name: 'Navigation',
        data() {
            return {
                shownavigation: true,
                brandName: "Eurosong Festival",
                id: "main-navigation",
                hiddenstate:true,
                links: [
                    {
                        linkText: "Home",
                        linkUrl: "home"
                    },
                    {
                        linkText: "Game",
                        linkUrl: "game"
                    },
                    {
                        linkText: "Ranking",
                        linkUrl: "ranking"
                    }
                ]
            }
        },
        methods: {
            goToPage(url) {
                this.$emit("change-page", url)
            },
            alertUser() {
                alert('Deze pagina bestaat niet!');
            }
        }
    }
</script>