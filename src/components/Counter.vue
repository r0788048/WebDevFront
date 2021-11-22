<template>

    <div v-if="isVisible">

        Buttoncounter: {{ count }}

        <button @click="addOne">
            + 1
        </button>

        <button @click="minOne">
            - 1
        </button>

        <button @click="hideCounter">
            Hide
        </button>

    </div>

</template>

<script>
    export default {
        name: "Counter",
        data() {
            return {
                count: 0,
                isVisible: true
            }
        },
        methods: {
            addOne() {
                this.count++;
            },
            minOne() {
                this.count--;
            },
            hideCounter() {
                this.isVisible = false
            }
        }
    }
</script>