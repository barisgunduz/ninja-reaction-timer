<template>
	<div>
		<p>Reaction time : {{ score }} ms</p>
		<p>{{ rank }}</p>
	</div>
</template>
<script>
export default {
	data() {
		return {
			rank: null,
		};
	},
	props: ["score"],
	mounted() {
		if (this.score < 250) {
			this.rank = "Ninja fingers";
		} else if (this.score >= 250 && this.rank < 400) {
			this.rank = "Not bad";
		} else if (this.score >= 400) {
			this.rank = "Fat fingers";
		}
	},
};
</script>
<style lang=""></style>
