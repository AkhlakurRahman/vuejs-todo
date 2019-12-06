<template>
	<div id="app">
		<Header />
		<AddTodo v-on:add-todo="addTodo" />
		<Todos v-bind:todos="todos" v-on:remove-todo="removeTodo" />
	</div>
</template>

<script>
import axios from 'axios';

import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import Header from './components/layout/Header';

export default {
	name: 'app',
	components: {
		Todos,
		AddTodo,
		Header
	},
	data() {
		return {
			todos: []
		};
	},
	methods: {
		removeTodo(id) {
			this.todos = this.todos.filter(todo => todo.id !== id);
		},

		addTodo(newTodo) {
			this.todos = [...this.todos, newTodo];
		},

		async created() {
			const res = await axios.get('https://jsonplaceholder.typicode.com/todos');

			this.todos = res.data;
		}
	}
};
</script>

<style>
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}

body {
	font-family: Arial, Helvetica, sans-serif;
	line-height: 1.4;
}
</style>
