<script setup>
import { ref } from "vue";
import Button from "./Button.vue";
import Modal from "./Modal/Modal.vue";
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
	rejectButtonVisibility: {
		type: Boolean,
		default: true,
	},
	settingsButtonTextColor: {
		type: String,
		default: "white",
	},
	settingsButtonBgColor: {
		type: String,
		default: "red",
	},
	settings: {
		type: Object,
		default: {},
	},
	policyText: {
		type: String,
		default:
			"Lorem ipsum dolor sit amet consectetur adipisicing elit. Veniam, quas accusantium deleniti aliquid et recusandae dignissimos non. Delectus, nam enim placeat impedit obcaecati magnam eum. Pariatur placeat culpa nesciunt provident vitae, aperiam velit. Odio eius aperiam voluptate molestias ex impedit mollitia architecto amet incidunt id, voluptatum voluptates deserunt, minus repellat.",
	},
});

const acceptButtonProperties = {
	title: props.acceptButtonTitle,
	textColor: props.acceptButtonTextColor,
	bgColor: props.acceptButtonBgColor,
};

const rejectButtonProperties = {
	title: props.rejectButtonTitle,
	textColor: props.rejectButtonTextColor,
	bgColor: props.rejectButtonBgColor,
};

const settingsButtonProperties = {
	title: "Settings",
	textColor: props.settingsButtonTextColor,
	bgColor: props.settingsButtonBgColor,
};

const emit = defineEmits(["buttonClick", "rejectClick"]);

const openModal = ref(false);

function clickHandler(value) {
	if (value == "Settings") {
		openModal.value = true;
	}
	emit("buttonClick", value);
	return;
}
</script>

<template>
	<div
		class="flex gap-1 justify-between items-center bg-slate-400 p-3 m-3 rounded-lg absolute bottom-0"
	>
		<div>
			<h3 class="text-xl font-semibold">Title</h3>
			<p>
				We baked some cookies that you have to accept, if you want to enjoy this
				website. It simply doesn't work without. In order to gather information
				and make improvements, we should use some third-party cookies too. Can
				we?
			</p>
		</div>
		<div class="button__container">
			<Button :properties="acceptButtonProperties" @click="clickHandler" />
			<Button
				:properties="rejectButtonProperties"
				@click="clickHandler"
				v-if="rejectButtonVisibility"
			/>
			<Button :properties="settingsButtonProperties" @click="clickHandler" />
		</div>
	</div>
	<div>
		<Modal
			:openModal="openModal"
			@close="openModal = false"
			:settings="props.settings"
			:policyText="policyText"
		/>
	</div>
</template>

<style lang="postcss" scoped>
.button__container {
	@apply flex gap-3;
}
</style>
