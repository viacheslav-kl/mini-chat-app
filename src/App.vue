<template>
	<div class="app">
		<Sidebar />
		<Chat />
	</div>
</template>

<script>
import Chat from './components/Chat.vue'
import Sidebar from './components/Sidebar.vue'

export default {
	components: {
		Sidebar,
		Chat,
	},
}
</script>

<style scoped>
.app {
	display: flex;
	height: 100vh;
}
</style>
