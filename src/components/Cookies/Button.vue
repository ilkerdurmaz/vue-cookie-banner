<script setup>
const props = defineProps(["properties"]);
const emit = defineEmits(["click"]);
const clickHandler = () => {
	emit("click", props.properties.title);
};
</script>

<template>
	<button
		class="button"
		@click="clickHandler"
		:disabled="props.properties.isDisabled"
	>
		{{ props.properties.title }}
	</button>
</template>

<style lang="postcss" scoped>
.button {
	@apply border-2 rounded-lg p-3 bg-slate-500 text-white;
}
</style>
