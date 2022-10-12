<script setup>
import { ref } from "vue";
import Policy from "./Policy.vue";
import Settings from "./Settings.vue";
const props = defineProps(["openModal", "settings", "policyText"]);
const selectedTab = ref("Settings");
const tabComps = {
	Policy,
	Settings,
};
</script>

<template>
	<div class="relative z-10" :class="{ hidden: !props.openModal }">
		<div
			class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
		></div>

		<div class="fixed inset-0 z-10 overflow-y-auto">
			<div
				class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
			>
				<div
					class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg"
				>
					<div class="modal-body">
						<div class="bg-slate-500 flex justify-between p-3">
							<h3 class="text-lg">Title</h3>
							<button @click="$emit('close')">✖</button>
						</div>
						<div class="flex py-3 text-center">
							<span class="tab tab-active" @click="selectedTab = 'Settings'"
								>Settings</span
							>
							<span class="tab tab-passive" @click="selectedTab = 'Policy'"
								>Cookies Policy</span
							>
						</div>
						<div class="tab-content">
							<component
								:is="tabComps[selectedTab]"
								:policyText="props.policyText"
								:settings="props.settings"
							></component>
						</div>
						<div class="bg-slate-500 flex items-center justify-between p-3">
							<p>Lorem ipsum dolor sit amet.</p>
							<button class="border-2 rounded-lg p-2">Save</button>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style lang="postcss" scoped>
.tab {
	@apply border-b-2 -mb-3 w-1/2;
}
.tab-active {
	@apply border-b-slate-900 font-semibold;
}
.tab-passive {
	@apply border-b-slate-200 cursor-pointer text-gray-500 hover:text-gray-800;
}

.tab-content {
	@apply p-3 bg-gray-100;
}
</style>
