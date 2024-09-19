<template>
	<div class="app">
		<Sidebar
			@toggleChatPanel="toggleSidebar"
			:collapsed="isSidebarCollapsed"
			:chats="chats"
			@selectChat="selectChat"
			:selectedChatId="selectedChatId"
		/>
		<div class="chat" v-if="selectedChatId">
			<Chat :selectedChat="selectedChat" @newMessage="updateLastMessage" />
		</div>
		<ChatEmpty v-else></ChatEmpty>
	</div>
</template>

<script>
import { computed, ref } from 'vue'
import Chat from './components/Chat.vue'
import ChatEmpty from './components/ChatEmpty.vue'
import Sidebar from './components/Sidebar.vue'

export default {
	components: {
		Sidebar,
		Chat,
		ChatEmpty,
	},
	setup() {
		const isSidebarCollapsed = ref(false)
		const selectedChatId = ref(null)
		const chats = ref([
			{
				id: 1,
				name: 'Чат 1',
				avatar: '/src/assets/avatar/Avatar.png',
				status: 'Online',
				lastMessage: 'Чат был обновлен',
				lastMessageTime: '19:48',
				newMessageCount: 1,
				isVerifyPerson: true,
			},
			{
				id: 2,
				name: 'Чат 2',
				avatar: '/src/assets/avatar/Avatar-1.png',
				status: 'в сети 2 часа назад',
				lastMessage: 'Ок, увидимся позже',
				lastMessageTime: '18:30',
				newMessageCount: 2,
				isVerifyPerson: false,
			},
			{
				id: 3,
				name: 'Чат 3',
				avatar: '/src/assets/avatar/Avatar-2.png',
				status: 'в сети 5 мин назад',
				lastMessage: 'Вы: Напомни, че там сделать надо ',
				lastMessageTime: '18:16',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
			{
				id: 4,
				name: 'Чат 3',
				avatar: '/src/assets/avatar/Avatar-3.png',
				status: 'в сети 3 мин назад',
				lastMessage: 'Погнали шары гонять',
				lastMessageTime: '18:02',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
			{
				id: 5,
				name: 'Чат 5',
				avatar: '/src/assets/avatar/Avatar-4.png',
				status: 'Online',
				lastMessage: 'Завтра напомни мне по поводу ди...',
				lastMessageTime: '17:42',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
			{
				id: 6,
				name: 'Чат 6',
				avatar: '/src/assets/avatar/Avatar-5.png',
				status: 'Online',
				lastMessage: 'Вы: Все готово ',
				lastMessageTime: '17:08',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
			{
				id: 7,
				name: 'Чат 7',
				avatar: '/src/assets/avatar/Avatar-6.png',
				status: 'Online',
				lastMessage: 'Канал создан',
				lastMessageTime: '16:15',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
			{
				id: 8,
				name: 'Чат 8',
				avatar: '/src/assets/avatar/Avatar-7.png',
				status: 'Online',
				lastMessage: 'Передай маме, что я буду к 8',
				lastMessageTime: 'Wed',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
			{
				id: 9,
				name: 'Чат 9',
				avatar: '/src/assets/avatar/Avatar-8.png',
				status: 'Online',
				lastMessage: 'Поехали отдыхать🏝',
				lastMessageTime: 'Tue',
				newMessageCount: 0,
				isVerifyPerson: false,
			},
		])

		const toggleSidebar = () => {
			isSidebarCollapsed.value = !isSidebarCollapsed.value
		}

		const selectedChat = computed(() => {
			return chats.value.find(chat => chat.id === selectedChatId.value) || {}
		})

		const selectChat = chatId => {
			selectedChatId.value = chatId
		}

		const updateLastMessage = (chatId, message) => {
			const chat = chats.value.find(chat => chat.id === chatId)
			if (chat) {
				chat.lastMessage = message
				chat.lastMessageTime = new Date().toLocaleTimeString([], {
					hour: '2-digit',
					minute: '2-digit',
				})
			}
		}

		return {
			isSidebarCollapsed,
			toggleSidebar,
			chats,
			selectedChatId,
			selectChat,
			selectedChat,
			updateLastMessage,
		}
	},
}
</script>

<style scoped>
.app {
	display: flex;
	height: 100vh;
}
</style>
