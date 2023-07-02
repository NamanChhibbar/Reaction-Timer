<template>
<div>Your reaction time: {{ props.result }}ms<br>{{ message }}</div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps(["result"]);
const message = computed(() => {
    if (props.result < 300) {
        return "God level speed!";
    } else if (props.result < 350) {
        return "Quick reflexes!";
    } else if (props.result < 400) {
        return "Average";
    } else {
        return "Too slow";
    }
})
</script>

<style scoped>
div {
    color: rgb(33, 203, 33);
    font-size: 25px;
    padding: 50px;
}
</style>
