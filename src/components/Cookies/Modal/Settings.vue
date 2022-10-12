<script setup>
import { ref } from "vue";
import SettingsItem from "./SettingsItem.vue";
const props = defineProps(["settings"]);
let updatedSettings = ref(props.settings);
const acceptAll = ref(true);

function settingChanged(value) {
	let settingIndex = updatedSettings.value.findIndex(
		(item) => item.name === value
	);
	if (settingIndex > -1) {
		updatedSettings.value[settingIndex].status =
			!updatedSettings.value[settingIndex].status;
	}

	acceptAll.value = updatedSettings.value.every((item) => item.status);
}

function acceptAllChanged() {
	console.log(acceptAll.value);
	if (!acceptAll.value) {
		updatedSettings.value = updatedSettings.value.map((item) => ({
			...item,
			status: false,
		}));
		return;
	}
	updatedSettings.value = updatedSettings.value.map((item) => ({
		...item,
		status: true,
	}));
	return;
}

function saveHandler() {
	localStorage.setItem("cookieSettings", JSON.stringify(updatedSettings.value));
}
</script>

<template>
	<div>
		<div class="flex my-3 justify-between">
			<h3>Accept All</h3>
			<label
				for="acceptall"
				class="inline-flex relative items-center cursor-pointer"
			>
				<input
					type="checkbox"
					:true-value="true"
					:false-value="false"
					id="acceptall"
					class="sr-only peer"
					v-model="acceptAll"
					@change="acceptAllChanged"
				/>
				<div
					class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-blue-600"
				></div>
			</label>
		</div>

		<SettingsItem
			v-for="setting in updatedSettings"
			:key="setting.key"
			:setting="setting"
			@settingChanged="settingChanged"
		/>

		<div class="flex items-center justify-between p-3">
			<p>Lorem ipsum dolor sit amet.</p>
			<button @click="saveHandler" class="border-2 rounded-lg p-2">
				Save and Accept
			</button>
		</div>
	</div>
</template>

<style lang="postcss" scoped></style>
