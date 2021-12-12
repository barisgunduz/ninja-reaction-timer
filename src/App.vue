<template>
	<h1>Ninja Reaction Timer</h1>
	<button @click="startGame" :disabled="isPlaying">Start</button>
	<Block v-if="isPlaying" :delay="delay" @end="endGame" />
	<Result v-if="showResults" :score="score" />
</template>

<script>
export default {
	name: "App",
	data() {
		return {
			isPlaying: false,
			delay: null,
			score: null,
			showResults: false,
		};
	},
	components: {
		Block: require("@/components/Block.vue").default,
		Result: require("@/components/Result.vue").default,
	},
	methods: {
		startGame() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
			this.showResults = false;
		},
		endGame(reactionTime) {
			this.score = reactionTime;
			this.showResults = true;
			this.isPlaying = false;
		},
	},
};
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
</style>
