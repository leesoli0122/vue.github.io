<template>
	<label>
		이름
		<!-- v-model="username" -->
		<input
			:value="modelValue"
			@input="event => $emit('update:modelValue', event.target.value)"
			type="text"
		/>
	</label>
</template>

<script>
import { computed } from 'vue';

export default {
	props: ['modelValue', 'label'],
	emits: ['update:modelValue'],
	setup(props, { emit }) {
		const value = computed({
			get() {
				return props.modelValue;
			},
			set(value) {
				emit('update:modelValue', value);
			},
		});
		return { value };
	},
};
</script>

<style></style>
