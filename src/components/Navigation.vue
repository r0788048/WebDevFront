<template>

    <nav class="c-nav" v-bind:id="id" v-if="shownavigation">

        <ul class="c-nav-list">

            <li class="c-nav-list-item" v-for="(link, index) in links" v-bind:key="index">

                <a @click="goToPage(link.linkUrl)">

                    {{ link.linkText }}

                </a>

            </li>

        </ul>

    </nav>

</template>

<script>
    export default {
        name: 'Navigation',
        data() {
            return {
                shownavigation: true,
                brandName: "Eurosong Festival",
                htmlTest: "<h1>Test H1</h1>",
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
            }
        }
    }
</script>