<template>
    
    <div v-bind:class=classtype v-if="isActive" @click="hide">

      {{ message }}

    </div>

</template>

<script>
export default {
    name: "Feedback",
    data() {
        return {
            isActive: true
        }
    },
    props: [
        "message",
        "classtype"
    ],
    methods: {
        hide() {
            this.isActive = false;
        }
    }
}
</script>