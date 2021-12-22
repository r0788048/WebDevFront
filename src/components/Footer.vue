<template>
    <div class="footer">
        <hr  style="width:100%" size="1" color=white>
        <nav class="c-ft" v-bind:id="id" v-if="shownavigation">

            <ul class="c-ft-list">

                <li class="c-ft-list-item" v-for="(link, index) in links" v-bind:key="index">

                    <a class="ft-href" href="javascript:alert('Deze pagina bestaat niet!');">

                        {{ link.linkText }}

                    </a>

                </li>

            </ul>

        </nav> 
        <div class="ft-text"> © EuroSong Voting App 2021-2022. All rights reserved. Website by r0788048. </div>
    </div>
</template>

<script>
    export default {
        name: 'Footer',
        data() {
            return {
                shownavigation: true,
                brandName: "Eurosong Festival",
                htmlTest: "<h1>Test H1</h1>",
                id: "main-navigation",
                hiddenstate:true,
                links: [
                    {
                        linkText: "Terms of Use",
                        linkUrl: "https://eurovision.tv/terms-of-use"
                    },
                    {
                        linkText: "Cookies & Privacy Policy",
                        linkUrl: "https://eurovision.tv/privacy-notice-cookie-information"
                    },
                    {
                        linkText: "Press",
                        linkUrl: "https://eurovision.tv/mediacentre"
                    },
                    {
                        linkText: "Support",
                        linkUrl: "https://eurovision.tv/support"
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