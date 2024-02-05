<template>
	<div id="app">
		<ProgressBar />
		<AddTasks />
		<div class="cardTasks">
			<CardTask />
		</div>
	</div>
</template>

<script>
import ProgressBar from '@/components/ProgressBar.vue'
import AddTasks from '@/components/AddTasks.vue'
import CardTask from '@/components/CardTask.vue'

export default {
	name: 'App',
	components: {
		ProgressBar,
		AddTasks,
		CardTask
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
		height: auto;
	}
	.cardTasks {
		width: 100%;
		display: flex;
		justify-content: center;
	}
</style>
