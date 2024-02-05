<template>
	<div id="app">
		<ProgressBar />
		<AddTasks />
	</div>
</template>

<script>
import ProgressBar from '@/components/ProgressBar.vue'
import AddTasks from '@/components/AddTasks.vue'

export default {
	name: 'App',
	components: {
		ProgressBar,
		AddTasks
	},
}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
		width: 100%;
	}
</style>
