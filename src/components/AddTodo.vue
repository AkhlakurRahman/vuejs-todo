<template>
	<div>
		<form @submit="addTodo">
			<input v-model="title" type="text" name="title" placeholder="Add Todo" />
			<input type="submit" value="Submit" class="btn" />
		</form>
	</div>
</template>

<script>
import uuid from 'uuid';

export default {
	name: 'AddTodo',
	data() {
		return {
			title: ''
		};
	},
	methods: {
		addTodo(e) {
			e.preventDefault();
			const newTodo = {
				id: uuid.v4(),
				title: this.title,
				completed: false
			};

			this.$emit('add-todo', newTodo);
			this.title = '';
		}
	}
};
</script>

<style scoped>
form {
	display: flex;
}

input[type='text'] {
	flex: 10;
	padding: 15px 10px;
	border: 1px solid #e3e3e3;
}

input[type='text']:focus {
	border: 1px solid #d3c2c2;
	outline: none;
}

input[type='submit'] {
	flex: 2;
	background: #d3c2c2;
	border: 1px solid #eee;
	color: #000;
	font-size: 18px;
}

input[type='submit']:hover {
	cursor: pointer;
	background: #e9cccc;
}
</style>
