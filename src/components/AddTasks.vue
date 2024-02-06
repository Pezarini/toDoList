<template>

  <div class="containerAddTasks">
	<input v-model="task" type="text" placeholder="Write your task..." @keyup.enter="sendTask" >
	<input @click="sendTask" type="button" value=">" id="Button">
  </div>

</template>

<script>
import connectComponents from '@/connectComponents';

export default {
	data() {
		return {
			task: ''
		}
	},
	methods: {
		sendTask() {
			if (!this.task) {
				return;
			}
			connectComponents.$emit('userWrittenTask', this.task);
			this.task = '';
		}
	},
}
</script>

<style scoped>
	.containerAddTasks {
		display: flex;
		justify-content: center;
		width: 100%;
	}
	.containerAddTasks input {
		font-size: x-large;
		text-align: center;
		width: 18%;
		margin-top: 60px;
		border-radius: 5px none;
	}

	#Button {
		width: 3%;
		background-color: rgb(42, 125, 242);
		border: none;
	}
</style>