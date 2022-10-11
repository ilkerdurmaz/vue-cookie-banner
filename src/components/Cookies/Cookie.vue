<script setup>
import Button from "./Button.vue";
const props = defineProps({
	acceptButtonTitle: {
		type: String,
		default: "Accept",
	},
	acceptButtonTextColor: {
		type: String,
		default: "black",
	},
	acceptButtonBgColor: {
		type: String,
		default: "white",
	},
	acceptButtonBorderColor: {
		type: String,
		default: "black",
	},
	rejectButtonTitle: {
		type: String,
		default: "Reject",
	},
	rejectButtonTextColor: {
		type: String,
		default: "white",
	},
	rejectButtonBgColor: {
		type: String,
		default: "red",
	},
	rejectButtonBorderColor: {
		type: String,
		default: "white",
	},
	rejectButtonDisabled: {
		type: String,
		default: "false",
	},
	acceptButtonDisabled: {
		type: String,
		default: "false",
	},
});

const acceptButtonProperties = {
	title: props.acceptButtonTitle,
	textColor: props.acceptButtonTextColor,
	bgColor: props.acceptButtonBgColor,
	borderColor: props.acceptButtonBorderColor,
	isDisabled: props.acceptButtonDisabled == "true",
};

const rejectButtonProperties = {
	title: props.rejectButtonTitle,
	textColor: props.rejectButtonTextColor,
	bgColor: props.rejectButtonBgColor,
	borderColor: props.rejectButtonBorderColor,
	isDisabled: props.rejectButtonDisabled == "true",
};

const emit = defineEmits(["buttonClick", "rejectClick"]);

function clickHandler(value) {
	emit("buttonClick", value);
}
</script>

<template>
	<div class="button__container">
		<Button :properties="acceptButtonProperties" @click="clickHandler" />
		<Button :properties="rejectButtonProperties" @click="clickHandler" />
	</div>
</template>

<style lang="postcss" scoped>
.button__container {
	@apply flex gap-3;
}
</style>
