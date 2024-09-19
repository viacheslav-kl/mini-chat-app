<template>
	<div class="chat-empty"><p>Выберите чат для начала общения</p></div>
</template>

<style lang="scss" scoped>
.chat-empty {
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: var(--color-blue);
	font-size: 18px;

	@media (max-width: 767px) {
		font-size: 14px;
	}

	p {
		padding: 5px 10px;
		background-color: var(--color-light);
		border-radius: var(--border-radius);
	}
}
</style>
