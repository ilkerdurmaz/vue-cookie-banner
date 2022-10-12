<script setup>
import Cookie from "./components/Cookies/Cookie.vue";
function clickHandler(val) {
	console.log(val);
}

const cookieSettings = [
	{
		name: "option1",
		status: true,
	},
	{
		name: "option2",
		status: true,
	},
	{
		name: "option3",
		status: true,
	},
	{
		name: "option4",
		status: true,
	},
	{
		name: "option5",
		status: true,
	},
];
</script>

<template>
	<div class="h-full">
		<Cookie
			:rejectButtonVisibility="true"
			@buttonClick="clickHandler"
			:settings="cookieSettings"
		/>
	</div>
</template>

<style lang="postcss" scoped></style>
