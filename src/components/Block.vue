<template>
    <div v-if="showBlock" @click="stopTimer">Click!</div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const showBlock = ref(false);
const timer = ref(null);
const reactionTime = ref(0);
const props = defineProps(["delay"]);
const emit = defineEmits(["end"]);

onMounted(() => {
    setTimeout(() => {
        showBlock.value = true;
        timer.value = setInterval(() => {
            reactionTime.value += 10;
        }, 10);
    }, props.delay);
})

function stopTimer() {
    clearInterval(timer.value);
    emit("end", reactionTime.value);
}
</script>

<style scoped>
    div {
        margin: 40px 200px;
        border: 2px solid black;
        border-radius: 20px;
        padding: 50px;
        background: rgb(2, 250, 68);
        font-size: 30px;
    }
</style>
