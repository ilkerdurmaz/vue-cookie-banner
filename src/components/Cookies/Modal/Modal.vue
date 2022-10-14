<script setup>
import { ref } from "vue";
import Policy from "./Policy.vue";
import Settings from "./Settings.vue";
const props = defineProps(["openModal", "settings", "policyText"]);
const emit = defineEmits(["saveCookies"])
const selectedTab = ref("Settings");


function saveHandler() {
	emit("saveCookies")
}
</script>

<template>
	<div class="relative z-10" :class="{ hidden: !props.openModal }">
		<div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>

		<div class="fixed inset-0 z-10 overflow-y-auto">
			<div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center items-center sm:p-0">
				<div
					class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg">
					<div class="modal-body ">
						<div class="bg-primary text-white flex justify-between p-3">
							<h3 class="text-lg">Customize Cookies</h3>
							<button @click="$emit('close')">✖</button>
						</div>
						<div class="flex py-3 text-center">
							<span class="tab" :class="[selectedTab === 'Settings' ? 'tab-active' : 'tab-passive']"
								@click="selectedTab = 'Settings'">Settings</span>
							<span class="tab" :class="[selectedTab === 'Policy' ? 'tab-active' : 'tab-passive']"
								@click="selectedTab = 'Policy'">Cookies Policy</span>
						</div>
						<div class="tab-content ">
							<Policy :policyText="props.policyText" v-if="selectedTab == 'Policy'" />
							<Settings :settings="props.settings" @saveCookies="saveHandler" v-else="selectedTab == 'Settings'" />
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
	@apply border-b-secondary text-secondary font-semibold;
}

.tab-passive {
	@apply border-b-tertiary cursor-pointer text-tertiary hover:text-secondary;
}

.tab-content {
	@apply p-3 bg-quaternary h-[46vh];
	
}

.modal-body {
		@apply h-[60vh] bg-quaternary flex flex-col;

}
</style>