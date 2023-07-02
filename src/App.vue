<template>
	<h1>Reaction Timer</h1>
	<button :disabled="isPlaying" @click="start">Play</button>
	<Block v-if="isPlaying" :delay="delay" @end="end" />
	<Result v-if="result" :result="result" />
</template>

<script setup>
import { ref } from "vue";
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

const isPlaying = ref(false);
const delay = ref(null);
const result = ref(null);

function start() {
	result.value = null;
	delay.value = 2000 + Math.random() * 4000;
	isPlaying.value = true;
}

function end(reactionTime) {
	isPlaying.value = false;
	result.value = reactionTime;
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

h1 {
	color: rgb(31, 216, 31);
}

button {
	background-color: rgb(43, 222, 16);
	font-size: 17px;
	padding: 5px 10px;
}
</style>
