<script setup>
import Cookie from "./components/Cookies/Cookie.vue";
function clickHandler(val) {
	console.log(val);
}
</script>

<template>
	<div>
		<h1 class="text-3xl font-bold underline">Hello world!</h1>
		<Cookie reject-button-disabled="true" @buttonClick="clickHandler" />
	</div>
</template>

<style lang="postcss" scoped></style>
