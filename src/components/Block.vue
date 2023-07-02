<template>
    <div v-if="showBlock" class="block" @click="stopTimer">Click!</div>
</template>

<script>
export default {
    name: "Block",
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    props: ["delay"],
    emits: ["end"],
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        }, this.delay);
    },
    methods: {
        stopTimer() {
            clearInterval(this.timer);
            this.$emit("end", this.reactionTime);
        }
    }
}
</script>

<style scoped>
    div {
        margin: 40px;
        border: 2px solid black;
        border-radius: 20px;
        padding: 100px 0px;
        background: rgb(2, 250, 68);
        font-size: 30px;
    }
</style>
