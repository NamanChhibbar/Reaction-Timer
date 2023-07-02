<template>
<div>Your reaction time: {{ props.result }}ms</div>
</template>

<script setup>
const props = defineProps(["result"]);
</script>

<style scoped>
div {
    color: rgb(33, 203, 33);
    font-size: 25px;
    padding: 50px;
}
</style>
