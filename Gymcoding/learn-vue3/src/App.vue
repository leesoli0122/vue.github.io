<template>
	<div>
		<p>{{ message }}</p>
		<button v-on:click="addMessage">click</button>
	</div>
</template>

<script>
import { reactive } from 'vue';

export default {
	setup() {
		let message = reactive('Hello vue!');
		const addMessage = () => {
			message = message + '!';
		};
		return {
			message,
			addMessage,
		};
	},
};
</script>

<style></style>
