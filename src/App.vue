<template>
	<h1>Reaction Timer</h1>
	<button :disabled="isPlaying" @click="start">Play</button>
	<Block v-if="isPlaying" :delay="delay" @end="end" />
	<p v-if="result">Your reaction time: {{ result }}ms</p>
</template>

<script>
import Block from "./components/Block.vue"

export default {
	name: "App",
	components: {Block},
	data() {
		return {
			isPlaying: false,
			delay: null,
			result: null
		}
	},
	methods: {
		start() {
			this.result = null;
			this.delay = 2000 +  Math.random() * 4000
			this.isPlaying = true;
		},
		end(reactionTime) {
			this.isPlaying = false;
			this.result = reactionTime;
		}
	}
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
