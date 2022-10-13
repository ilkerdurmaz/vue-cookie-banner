<script setup>
defineProps(["policyText"]);
</script>

<template>
	<div class="px-3 py-2 bg-quaternary rounded text-primary font-medium border-2 border-secondary border-opacity-20 overflow-auto h-[46vh]">
		{{ policyText }}
	</div>
</template>

<style lang="postcss" scoped></style>
