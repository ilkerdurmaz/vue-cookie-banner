<script setup>
import SettingsItem from "./SettingsItem.vue";
const props = defineProps(["settings"]);
let updatedSettings = structuredClone(props.settings);

function settingChanged(value) {
	let settingIndex = updatedSettings.findIndex((item) => item.name === value);
	if (settingIndex > -1) {
		updatedSettings[settingIndex].status =
			!updatedSettings[settingIndex].status;
		localStorage.setItem("cookieSettings", JSON.stringify(updatedSettings));
	}
}
</script>

<template>
	<div>
		<SettingsItem
			v-for="setting in settings"
			:key="setting.key"
			:setting="setting"
			@settingChanged="settingChanged"
		/>
	</div>
</template>

<style lang="postcss" scoped></style>
