<template>

    <nav class="c-nav" v-bind:id="id" v-if="shownavigation">

        <span v-html=htmlTest v-bind:hidden="hiddenstate"></span>

        <ul class="c-nav-list">

            <li class="c-nav-list-item" v-for="(link, index) in links" v-bind:key="index">

                <a v-bind:href="link.linkUrl">

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
                        linkUrl: "/home"
                    },
                    {
                        linkText: "Contact",
                        linkUrl: "/contact"
                    },
                    {
                        linkText: "Shop",
                        linkUrl: "/shop"
                    }
                ]
            }
        }
    }
</script>