<template>
	<div class="app">
		<Sidebar @toggleChatPanel="toggleSidebar" :collapsed="isSidebarCollapsed" />
		<Chat />
	</div>
</template>

<script>
import { ref } from 'vue'
import Chat from './components/Chat.vue'
import Sidebar from './components/Sidebar.vue'

export default {
	components: {
		Sidebar,
		Chat,
	},
	setup() {
		const isSidebarCollapsed = ref(false)

		const toggleSidebar = () => {
			isSidebarCollapsed.value = !isSidebarCollapsed.value
		}

		return { isSidebarCollapsed, toggleSidebar }
	},
}
</script>

<style scoped>
.app {
	display: flex;
	height: 100vh;
}
</style>
