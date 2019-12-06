<template>
	<div class="todo-item" v-bind:class="{ 'is-completed': todo.completed }">
		<p>
			<input type="checkbox" v-on:change="markComplete" />
			{{ todo.title }}
		</p>
		<button class="delete-item" @click="$emit('remove-todo', todo.id)">
			X
		</button>
	</div>
</template>

<script>
export default {
	name: 'TodoItem',
	props: ['todo'],
	methods: {
		markComplete() {
			this.todo.completed = !this.todo.completed;
		}
	}
};
</script>

<style scoped>
.todo-item {
	background: #e3e3e3;
	font-size: 18px;
	padding: 20px 10px;
	border-bottom: 1px solid #eeeeee;
	text-align: center;
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.is-completed {
	text-decoration: line-through;
}

.delete-item {
	background: rgb(153, 26, 26);
	padding: 12px;
	font-size: 18px;
	border: none;
	cursor: pointer;
	color: #ffffff;
	border-radius: 3px;
}
</style>
