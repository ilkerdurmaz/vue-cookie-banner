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
		<Cookie :rejectButtonVisibility="true" @buttonClick="clickHandler" :settings="cookieSettings" title="Title"
			description="We baked some cookies that you have to accept, if you want to enjoy this
					website. It simply doesn't work without. In order to gather information
					and make improvements, we should use some third-party cookies too. Can
					we?" />
	</div>
</template>

<style lang="postcss" scoped>

</style>
